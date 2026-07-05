1、启动ubuntu   
	    wsl --install -d Ubuntu-26.04
2、更新软件包
	    sudo apt update && sudo apt upgrade -y
3、安装proxychains4
	    sudo apt install proxychains4 -y
	     vi /etc/proxychains4.conf
	     socks5 192.168.0.240     7897
	     
	     启动 SSH 代理配合使用 
	     ssh -D 1080 -N -f user@server
          配置（添加代理） 
          echo "socks5 127.0.0.1 1080" >> /etc/proxychains4.conf
          
	     添加到 ~/.bashrc 
	     alias pc='proxychains4' 
	     alias docker-pull='proxychains4 docker pull'
	     
	      proxychains4 curl https://ip.sb
	      pc curl https://ip.sb
	      
