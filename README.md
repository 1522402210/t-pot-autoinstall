# 自动安装 T-Pot  中国区加速 
感谢 [T-Pot 17.10](http://dtag-dev-sec.github.io/mediator/feature/2017/11/07/t-pot-17.10.html) ，感谢[n3uz](https://github.com/n3uz/t-pot-autoinstall)。

修改如下：

```
1、修改Ubuntu源为163源。
2、修改pip安装源为清华源。
3、修改git源为coding。
4、docker增加aliyun mirror
```

脚本在ubuntu16.04 下测试通过。

## 部署前置条件

- 准备普通用户，并为普通用户创建公私钥，用于密钥登录。
- root运行安装脚本

以普通用户z为例

```
z@ubuntu:~$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/z/.ssh/id_rsa):
Created directory '/home/z/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/z/.ssh/id_rsa.
Your public key has been saved in /home/z/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:ZEVXpFGTbX+e/RoGkF/XxN9McBKt7MUvaZxAZ7XL/Tw z@ubuntu
The key's randomart image is:
+---[RSA 2048]----+
|         .o o+OO+|
|         . o.o+=O|
|        o o..+.B*|
|       o   o..+.@|
|        S   o+ B*|
|             .Bo=|
|             .oE+|
|             . .o|
|              .. |
+----[SHA256]-----+

z@ubuntu:~$ ls -la ./.ssh
total 16
drwx------ 2 z z 4096 Oct 26 14:56 .
drwxr-xr-x 4 z z 4096 Oct 26 14:56 ..
-rw------- 1 z z 1766 Oct 26 14:56 id_rsa
-rw-r--r-- 1 z z  390 Oct 26 14:56 id_rsa.pub

```

添加公钥

```
z@ubuntu:~$ cat /home/z/.ssh/id_rsa.pub >> /home/z/.ssh/authorized_keys
```

保存私钥/home/z/.ssh/id_rsa 文件，用于后面的登录。



## 安装建议

* 执行install.sh之前先执行如下命令，执行完毕之后再运行install.sh

  ```
  apt-get install python2.7
  pip install -i https://pypi.tuna.tsinghua.edu.cn/simple --upgrade pip && hash -r pip
  pip install -i https://pypi.tuna.tsinghua.edu.cn/simple --upgrade setuptools
  pip install docker-compose==1.16.1 
  pip install elasticsearch-curator==5.2.0 
  
  apt-get install nodejs npm
  npm install https://github.com/t3chn0m4g3/wetty -g
  npm install https://github.com/t3chn0m4g3/elasticsearch-dump -g
  ```

  

