# MySQL�����������
2015.06.13

### 1.��������

Mysql����������ĩβ����Ҫ�ԷֺŽ�����һ��������Էֳɶ�����д��

+ �������ݿ⣺mysql �Cu root �Cp��
+ �鿴�������ݿ⣺show databases;
+ �������ݿ⣺create database databaeName;
+ ѡ�����ݿ⣺use databaseName;ֻ��ѡ�����ݿ����ܽ�����ص����ݿ������
+ ɾ�����ݿ⣺drop database databaseName;
+ ������create table use( id varchar(10) primary key, name varchar(10) not null);
+ �鿴���б�show tables;
+ ɾ����drop table tableName;

### 2.�ַ���

MySQL�ڰ�װʱ�ַ���Ĭ����latin����֧�����ġ�����ʵ�ʿ��������л�����ܴ�����⣬����һ����Ҫ���ַ�����ʽ�޸�Ϊutf8����windows�а�װʱ����ѡ��Ĭ�ϵ��ַ���Ϊutf8������linux��ֱ��ʹ�����װ�ǲ���ѡ��ģ�����linux���޸��ַ����ķ�ʽ�Ƚϸ��ӣ��Թ����ζ��������⣩�����˾��ÿ��Գ���ת��ķ�ʽ������Java��URLEncoder��URLDecoder������Hbase�д����ݵ�Bytes.toBytes�����ȣ������Ͳ�������������⣬����֮���Ǳ����������Ҫ����ʱ�䡣

### 3.�����vi����

��Ȼͼ�λ��û������޸��ļ��ܷ��㣬����Щʱ�����ͨ��vi���޸ģ�����vi��Ȼǿ��ȴҲ���ӡ��ǳ������ļ���vi����Ժ�Ҫ����ѧ�ɡ�

vi������״̬��input mode��command mode��line mode��

1. �����ļ���vi filename��
2. ����viʱ���Զ���command mode����i��command mode����input mode��
3. ��input mode���������ļ��޸�һ����
4. �޸���Ϻ󣬰�Esc���ص�command mode��
5. ����ZZ�浵���˳�vi�������;�������⣬����ͨ������:q!ǿ���뿪���������κ��޸ģ���