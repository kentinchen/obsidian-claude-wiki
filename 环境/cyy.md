xc_hlw_转发服务器   172.63.132.49
xc_hlw_开发环境      172.63.132.144
xc_hlw_测试环境      172.63.132.33
xc_hlw_生产环境      ACK K8S集群

1、xc_hlw_转发服务器   172.63.132.49
	 yum install -y xorg-x11-xauth && xdpyinfo
     yum install kubectl -y
     yum install haproxy -y && ls  /etc/haproxy/     
     docker、nginx (/opt/nginx_install/install.sh,配置在/nginx/)   

2、xc_hlw_开发环境      172.63.132.144
     1、安装Clash Verge、cpolar、Easytier
     2、安装UniGetUI、FlyEnv
     3、安装Lens、kubectl
     
3、xc_hlw_测试环境（IUT-Server)
	安装软件源：rpm -Uvh https://mirrors.aliyun.com/alinux/4/updates/x86_64/os/Packages/alinux-repos-4-14.1.alnx4.x86_64.rpm
    软件安装： git、docker、FlyEnv、node、buzz、SupaBase、
         yum install -y git docker  FlyEnv-4.17.1-x64.rpm        
         export http_proxy="socks5://172.63.132.33:7897"
         export https_proxy="socks5://172.63.132.33:7897"
         git config --global http.proxy socks5://172.63.132.33:7897
	     git config --global https.proxy socks5://172.63.132.33:7897 
         curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
         nvm install --lts && nvm use --lts      
	    curl -fsSL https://github.com/cashapp/hermit/releases/download/stable/install.sh | /bin/bash
	    whereis hermit &&  hermit --version
	安装supabase
	    npm install supabase --save-dev && supabase init && npx supabase start   
	安装buzz
	    cd /opt/buzz && git pull
		. ./bin/activate-hermit
	    just setup && just build
    docker服务：
        docker run -d -p 8000:8000 --name ddddocr-api-container ddddocr-api
        curl -X POST -F "file=@1.png" http://172.63.132.144:8000/ocr

4、xc_hlw_生产环境