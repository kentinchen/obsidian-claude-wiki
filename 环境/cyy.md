xc_hlw_转发服务器   172.63.132.49
xc_hlw_开发环境      172.63.132.33
xc_hlw_测试环境      172.63.132.144
xc_hlw_生产环境      ACK K8S集群

1、xc_hlw_转发服务器   172.63.132.49
	 yum install -y xorg-x11-xauth && xdpyinfo
     yum install kubectl helm kustomize -y
     yum install haproxy -y && ls  /etc/haproxy/     
     /opt/nginx_install/install.sh (docker、nginx安装启动、配置在/nginx/)   

2、xc_hlw_开发环境      172.63.132.33
     1、安装Clash Verge、cpolar、Easytier
     2、安装UniGetUI、FlyEnv
     3、安装Lens、kubectl、kustomize、helm、istio、kagent
     
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
	 安装k8s服务：
curl -C - -LO --retry 10 https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64  
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64 && minikube version    
source /opt/proxy.sh && minikube start --embed-certs --force
curl -C - -LO --retry 10 "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"  
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl && rm -f kubectl && kubectl version --client    
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash  && helm version    
curl -s "https://raw.githubusercontent.com/kubernetes-sigs/kustomize/master/hack/install_kustomize.sh"  | bash && sudo mv kustomize /usr/local/bin
curl https://raw.githubusercontent.com/kagent-dev/kagent/refs/heads/main/scripts/get-kagent | bash
	 安装kagent
export OPENAI_API_KEY="sk-你的密钥"  &&  kagent install --profile demo
helm install kagent-crds oci://ghcr.io/kagent-dev/kagent/helm/kagent-crds \
--namespace kagent --create-namespace
helm install kagent oci://ghcr.io/kagent-dev/kagent/helm/kagent \
--namespace kagent --create-namespace \
--set providers.default=ollama \
--set providers.ollama.baseUrl=https://openrouter.ai/api/v1 \
--set providers.ollama.apiKey=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

//kagent dashboard
kubectl port-forward -n kagent service/kagent-ui 8082:8080
netsh interface portproxy add v4tov4 listenport=8082 listenaddress=0.0.0.0 connectport=8082 connectaddress=(wsl hostname -I)

kubectl create secret generic kagent-openai -n kagent --from-literal=OPENAI_API_KEY="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"
kubectl apply -f- <<EOF
apiVersion: kagent.dev/v1alpha2
kind: ModelConfig
metadata:
  name: default-model-config
  namespace: kagent
spec:
  apiKeySecret: kagent-openai
  apiKeySecretKey: OPENAI_API_KEY
  model: nvidia/nemotron-3-super-120b-a12b:free
  provider: OpenAI
  openAI:
    baseUrl: "https://openrouter.ai/api/v1"    
EOF

kagent invoke -t "请在集群中安装 Istio，使用 default profile，并启用 Ambient Mesh" --agent istio-agent

4、xc_hlw_生产环境