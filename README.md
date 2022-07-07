# pzyJenkins
一些jenkins使用记录

1.ubuntu20.04安装jenkins
将存储库密钥添加到系统：
  wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | sudo apt-key add -

sudo sh -c ‘echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list’

3.sudo apt-get update 执行update后如果提示GPG错误，参考该文档解决https://2hux1nb0.github.io/2021/12/16/ubuntu安装Jenkins报GPG错误解决办法

4.sudo apt-get install jenkins

5.配置Jenkins端口：修改/etc/default/jenkins, 配置默认端口8080改为8082（或者其他不冲突的端口号），
注：这里jenkins默认只读的，端口默认8080会和tomcat或Apache冲突，需要用root身份进行修改 sudo vim /etc/default/jenkins
改为：HTTP_PORT=8082

还有一个文件也要改8082，在/etc/init.d/jenkins中，一共这两个地方，改完保存退出，重启Jenkins。

Jenkins启动/重启/停止命令：

查看状态：systemctl status jenkins.service

启动 service jenkins start

重启 service jenkins restart

停止 service jenkins stop

查看Jenkins进程：ps -ef |grep jenkins


1.ubuntu卸载jenkins
(移除服务，删除安装包，删除配置和数据)

a.apt remove jenkins
b.apt remove --auto-remove jenkins
c.apt purge jenkins
d.apt purge --auto-remove jenkins

