---
layout: default
---

## Kernel 内存管理之kmem_cache奇旅
2018.06.23

|![kernel-memory](./../images/kernel-memory.jpg?raw=true)<br>奇幻旅行，图片来源：电影《圆梦巨人》|

### 背景
fscrypt_info中参数ci_essiv_tfm未初始化，导致在循环通过kmem_cache_alloc从高速缓存中获取数据时，拿到之前的脏数据，导致在通过crypto_free_cipher释放ci_essiv_tfm时出现PINIC。

crypto_free_cipher<br>
|-->crypto_cipher_tfm<br>
|-->crypto_free_tfm<br>
&nbsp;&nbsp;|-->crypto_destory_tfm<br>
&nbsp;&nbsp;&nbsp;&nbsp;|-->crypto_exit_ops<br>

kmem_cache_free<br>
|-->__cache_free<br>
&nbsp;&nbsp;|-->cpu_cache_get<br>
&nbsp;&nbsp;|-->kmemcheck_slab_free<br>
&nbsp;&nbsp;&nbsp;&nbsp;|-->kmemcheck_mark_freed<br>
&nbsp;&nbsp;|-->ac_put_obj<br>
&nbsp;&nbsp;&nbsp;&nbsp;|-->__ac_put_obj<br>

>> kmemcheck_mark_freedARM平台不做任何处理，x86平台会调用mark_shadow方法对free中内存数据进行复写。

### Example
```c
#define STRUCT_LEN   (128)
#define MAX_NAME_LEN (100)

static struct kmem_cache *my_cachep = NULL;

struct user_info {
	char name[MAX_NAME_LEN];
	u8   age;
	char sex;
	char reserved[STRUCT_LEN-MAX_NAME_LEN-2]
} __packed;

int slab_demo (void)
{
	char *cache_name = "user_info";
	void *object = NULL;
	my_cachep = kmem_cache_create(cache_name,
	                              sizeof(struct user_info),
                                      0, 0, NULL);
	if (!my_cachep) {
		pr_err("Alloc cache failed.\n");
		goto fail_alloc_cache;
	}

	pr_info("Cache name is %s\n", kmem_cache_name(my_cachep));
	pr_info("Cache object size is %d\n", kmem_cache_size(my_cachep));
	
	object = kmem_cache_alloc(my_cachep, GFP_KERNEL);
	if(object)
		kmem_cache_free( my_cachep, object );
	else
		pr_err("Alloc object from cache failed.\n");

fail_alloc_cache:
	if(my_cachep)
		kmem_cache_destroy(my_cachep);

	return 0;
}
```
