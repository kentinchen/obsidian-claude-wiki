xc_hlw_转发服务器   172.63.132.49
xc_hlw_开发环境      172.63.132.33
xc_hlw_测试环境      172.63.132.144
xc_hlw_生产环境      ACK K8S集群

1、xc_hlw_转发服务器   172.63.132.49
	 yum install -y xorg-x11-xauth && xdpyinfo
     yum install kubectl helm kustomize -y
     yum install haproxy -y && ls  /etc/haproxy/     
     /opt/nginx_install/install.sh (docker、nginx安装启动、配置在/nginx/)   