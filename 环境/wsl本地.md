1、启动ubuntu   
	    wsl --install -d Ubuntu-26.04
2、更新软件包
	    sudo apt update && sudo apt upgrade -y
3、安装proxychains4
	    sudo apt install proxychains4 -y 	     	      
4、网络访问
       netsh interface portproxy add v4tov4 listenport=<yourPortToForward> listenaddress=0.0.0.0 connectport=<yourPortToConnectToInWSL> connectaddress=(wsl hostname -I)