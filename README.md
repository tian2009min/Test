# 解决Github打不开或打开慢的问题
1. 修改本地hosts文件
（1）windows系统的hosts文件的位置如下：C:\Windows\System32\drivers\etc\hosts
mac/linux系统的hosts文件的位置如下：/etc/hosts

（2）IP获取如下：
1、确定github网站的ip： https://ipaddress.com/website/github.com
2、确定域名IP： https://ipaddress.com/website/github.global.ssl.fastly.net
3、确定静态资源ip：https://ipaddress.com/website/assets-cdn.github.com

（3）最终修改文件内容
192.30.253.112 Github.com
192.30.253.113 Github.com
151.101.185.194 github.global.ssl.fastly.net
151.101.13.194 github.global.ssl.fastly.net
151.101.12.153	assets-cdn.github.com
151.101.84.153	assets-cdn.github.com
151.101.111.153	assets-cdn.github.com

2. 刷新DNS，更新DNS缓存
打开cmd 输入 ipconfig /flushdns

参考网站：
完美解决github访问速度慢：https://zhuanlan.zhihu.com/p/93436925
解决浏览器打不开github网站常用方法：https://zhuanlan.zhihu.com/p/36154464

# OpenSSL SSL_read: Connection was reset, errno 10054 
1、取消ssl设置
git config --global http.sslVerify "false"

2、去github官网上生成个人令牌
原因：根据 GitHub 官方说法，从 2021 年 8 月 13 日开始，他们将在对 Git 操作进行身份验证时不再接受帐户密码，并将要求使用基于令牌（token）的身份验证。
例如：个人访问令牌（针对开发人员）或 OAuth 或 GitHub 应用程序安装令牌（针对集成商） GitHub.com 上所有经过身份验证的 Git 操作。
（1）简单来说就是将原来输入密码的地方，改成输入 toke 即可。因此首先我们需要创建 token，登录我们的 github，找到 settings：
（2）点击“Developer settings”菜单项。
（3）接着点击“Personal access tokens”菜单项，然后点击右侧的“Generate new token”按钮。
（4）将自己的访问令牌Copy备份保存下来。

3、文件太大，执行命令：git config http.postBuffer 5242880003
参考网站：https://www.hangge.com/blog/cache/detail_3139.html
其他参考网址：https://www.cnblogs.com/fairylyl/p/15059437.html

# GitGui注意项
1、相关学习网址，如下：
https://www.runoob.com/w3cnote/git-gui-window.html

2、git clone https://github.com/tian2009min/Test.git
该操作会自动将配置及相关信息加入到gitgui中。

3、添加、修改、删除文件/内容，更改后，操作步骤，如下：
（1）Stage Changed：缓存改动（即：暂存）
（2）Commit：提交
（3）Push：上传（即：推送）【该功能执行，直接到了对应的服务器上，例如：github上】