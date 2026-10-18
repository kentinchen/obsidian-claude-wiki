	%USERPROFILE%\.proxychains\proxychains.conf
	C:\ProgramData\Proxychains\proxychains.conf

	vi /etc/proxychains4.conf
	socks5 192.168.0.240     7897
	     
	ssh -D 1080 -N -f user@server
    echo "socks5 127.0.0.1 1080" >> /etc/proxychains4.conf
          
	添加到 ~/.bashrc 
	alias pc='proxychains4' 
	alias docker-pull='proxychains4 docker pull'
	     
	proxychains4 curl https://ip.sb
	pc curl https://ip.sb