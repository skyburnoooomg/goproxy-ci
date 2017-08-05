# goproxy-ci
#安装代码
curl -L git.io/get-goproxy-vps.sh | bash
#启动代码
#./goproxy-vps.sh start


做一个简易安装手册
1.vps 自行选择购买，不做推荐，建议内存不要太低（256mb，解压都成问题）
2.申请域名，很多选择，.tk，.ml等是免费域名
3.dns解析（可选，适合国外申请的域名，加快解析速度），可选cloudxn，dnspod等
4.安装goproxy-vps，可以用curl -L git.io/get-goproxy-vps | bash，输入域名即可，不过配置没有https选项，需要自行添加
推荐是用wget https://github.com/phuslu/goproxy-ci/releases/download/r1474/goproxy-vps_linux_amd64-rxxx.tar.xz （xxx为版本号），然后tar -xJvf goproxy-vps_linux_amd64-rxxx.tar.gz ( 解压失败看看是不是xz-utils没装）
5.（上面用第一条命令的，跳过此步）把goproxy-vps.toml 中example.org 和proxy.example.org换成你的域名（一样的），把http的选项去掉
6.验证问题，听说pam不太听话，可能和系统有关吧，自测没问题，root是不能验证的，用adduser添加用户。也可以使用其他验证htpasswd（自行google，不难使用），client ca pem（比较复杂，适合对签发证书比较了解者）
6.启动 前端：在goproxy-vps目录执行./goproxy-vps 后台：./goproxy-vps.sh start 抓日志cat goproxy-vps.log
7.客户端
chrome://flags/#ssl-version-max 的 tls1.3 支持 搭SwitchyOmega 选择https类型，填上域名，端口443
stunnel 跨平台软件
drony（安卓）
goproxy-vps(推荐，因为一些软件不支持tls1.3，会出现403错误）
把配置文件的http选项留下，其余选项删除，parent_proxy中的example.org换成你的域名，如有pam、htpasswd验证，格式为https://用户名:密码@域名，如有端口重定向，则https://用户名:密码@域名: 端口
8. 祝gp爱好者使用愉快，感谢社长
