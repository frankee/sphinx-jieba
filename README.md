# sphinx-jieba
Sphinx for Chinese with cppJieba

仿照[Sphinx for Chinese](https://github.com/eric1688/sphinx.git)，基于sphinx 2.2.9版本，结合cppJieba分词系统，让sphinx支持中文。


## 安装
### 解压

```
$ git clone https://github.com/eric1688/sphinx
$ cd sphinx
```

### 编译（假设安装到/usr/local/sphinx目录，下文同）

```
$ ./configure --prefix=/usr/local/sphinx
--prefix 指定安装路径
--with-mysql 编译mysql支持
--with-pgsql 编译pgsql支持
$ make
$ make install
```

## 配置中文支持

### 修改sphinx.conf索引配置文件

在索引配置项中添加以下两项：

```
charset_type = utf-8
chinese_dictionary = /usr/local/sphinx/etc/xdict
```

**注意在source部分一定加上如下字段，否则中文分词无法起作用。**

```
sql_query_pre = SET NAMES utf8
```

## TODOs:

1. 在index时，添加同义词功能
    a. 本身在Sphinx GetToken时可以返回多个同义Token
    b. 增加同义词典
2. 字典支持二进制形式
3. cmake make sure the expat and int64_t varible set.
