1、启动ubuntu   
	    wsl --install -d Ubuntu-26.04
2、更新软件包
	    sudo apt update && sudo apt upgrade -y
3、安装proxychains4
	sudo apt install proxychains4 -y      
	
4、网络访问
       netsh interface portproxy add v4tov4 listenport=<yourPortToForward> listenaddress=0.0.0.0 connectport=<yourPortToConnectToInWSL> connectaddress=(wsl hostname -I)


# 添加 Docker 官方 GPG 密钥
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg 
# 添加 Docker APT 仓库
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null 
# 安装 Docker Engine
sudo apt update && sudo apt install -y docker-ce docker-ce-cli containerd.io