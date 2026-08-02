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