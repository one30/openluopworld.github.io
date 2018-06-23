---
layout: default
---

## Kernel 内存管理之slab
2018.06.23

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
