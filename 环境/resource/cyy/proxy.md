1、proxy.sh
#!/bin/bash
export HTTP_PROXY="http://172.63.132.33:10808"  
export HTTPS_PROXY="http://172.63.132.33:10808"  
export NO_PROXY="localhost,127.0.0.1,::1,10.96.0.0/12,192.168.0.0/16,192.168.49.0/24,192.168.58.0/24,host.docker.internal,.svc,.cluster.local"  
export no_proxy="$NO_PROXY"
	
2、proxy.env
HTTP_PROXY="http://172.63.132.33:10808"  
HTTPS_PROXY="http://172.63.132.33:10808"  
NO_PROXY="localhost,127.0.0.1,::1,10.96.0.0/12,192.168.0.0/16,192.168.49.0/24,192.168.58.0/24,host.docker.internal,.svc,.cluster.local"  
no_proxy="$NO_PROXY"

3、minikube自动启动
vi /etc/systemd/system/minikube.service
[Unit]  
Description=Start Minikube Cluster  
After=network-online.target docker.service  
Wants=network-online.target docker.service  
  
[Service]  
Type=oneshot  
RemainAfterExit=yes  
#ExecStartPre=/opt/proxy.sh  
EnvironmentFile=/opt/proxy.env  
ExecStart=/usr/local/bin/minikube start --embed-certs  --listen-address=0.0.0.0 --apiserver-ips=172.63.132.144 --force  
ExecStop=/usr/local/bin/minikube stop  
User=root  
Group=root  
  
[Install]  
WantedBy=multi-user.target

systemctl daemon-reload && systemctl restart minikube.service

4、git配置
git config --list
git config --global --list

取消专属代理设置
git config --global --unset http.proxy
git config --global --unset https.proxy

设置全局代理（适用于所有地址）
git config --global http.proxy socks5://172.63.132.33:7897
git config --global https.proxy socks5://172.63.132.33:7897

加速站
git config --global url."https://hub.fastgit.xyz/".insteadOf https://github.com/
git config --global --unset url."https://hub.fastgit.xyz/".insteadOf