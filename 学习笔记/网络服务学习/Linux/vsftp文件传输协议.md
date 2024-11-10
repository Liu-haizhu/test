
##### 定义：
用于internet上的文件双向传输，前身是ftp，由于ftp是明文传输，具有一定的危险性，所以推出了vsftp。

##### 特点：
执行相关的命令需要上层程序的许可，拥有chroot功能，可以改变用户的根目录。

##### 开放端口：
21:通常用于vsftp建立连接时。
20:用于建立连接后，用户上传和下载数据。

##### 工作模式：
port主动模式：客户端通过21端口向服务器端发起建立连接的请求，然后客户端随机开放一个端口并告知服务端，服务端和客户端通过随机开放的端口进行数据的传输。
passive被动模式：客户端通过21端口想服务器端发起建立连接的请求，随后服务端随机开放一个端口并告知客户端，服务端和客户端通过服务器端开启的随机端口进行数据的传输。


##### 登录验证方式：
匿名用户登录：指任何人可以通过匿名账号进行登录，不需要进行密码验证。匿名账号ftp、anonymous，匿名用户登录后根目录：/var/ftp

添加用户登录不能用于登录：
useradd -s /sbin/nologin []

##### 配置文件/etc/vsftpd/vsftpd.conf

```js
#允许匿名用户登录
anonymous_enable=YES

#匿名用户根目录
anon_root=/var/ftp

#允许本地用户登录
local_enable=YES

#全局配置，凡是登录进来的用户都有写的权限
write_enable=YES

#允许匿名用户上传
anon_upload_enable=YES

#允许匿名用户创建目录，拥有写的权限
anon_mkdir_write_enable=YES

#允许匿名用户拥有其他权限，删除、覆盖、重命名
anon_other_write_enable=YES

#虚拟用户创建目录的默认权限为755，这里umask是反掩码与在目录里面ll看到的权限相反 umask022=755
anon_umask=022

#禁止指定邮箱登录文件位置，同时开启邮箱验证登录。配合下面的命令一起使用
banned_email_file=/etc/vsftpd/banner_emails

#开启此功能需要进行登录邮箱验证，在配置文件下创建禁止登录邮箱的文件，出现在文件中的邮箱禁止登陆
deny_email_enable=YES





```


##### 匿名用户登录，并有上传和写入的权限

匿名用户登录后的根目录为/var/ftp，在这个目录下匿名用户只有下载的权限。可以在/var/ftp这个根目录下创建一个目录并给与777的权限，修改vsftpd.conf配置文件。匿名用户在/var/ftp/下创建的目录中即可上传文件和创建目录。

```js
修改配置文件
annonymous_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES

```

