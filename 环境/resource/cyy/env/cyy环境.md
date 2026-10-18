xc_hlw_转发服务器   172.63.132.49
xc_hlw_开发环境      172.63.132.33 Administrator Super1900.
xc_hlw_测试环境      172.63.132.144
xc_hlw_生产环境      ACK K8S集群

172.63.132.21 root xxxxx
172.62.18.182 mysql  xxxx
metrics.cms.ops.inter.xc-cdcloud.com                                    172.63.36.151 172.63.132.47 172.63.73.95
internal.asapi.cn-cd-cdxchlw-d01.ops.inter.xc-cdcloud.com  172.63.36.153 172.63.132.48 172.63.73.95

1、xc_hlw_转发服务器   172.63.132.49
	 yum install -y xorg-x11-xauth && xdpyinfo
     yum install kubectl helm kustomize -y
     yum install haproxy -y && ls  /etc/haproxy/     
     /opt/nginx_install/install.sh (docker、nginx安装启动、配置在/nginx/)   

2、原环境
172.60.105.35:22、172.60.105.71:24022(172.60.142.240)    dev
172.60.105.35:62222(172.60.142.10)        k8s(6节点)
172.60.142.8                                             k8s(1节点)
scp -P 62222 -i id_rsa root@172.60.105.35:/root/software/kafka_2.13-3.9.0.tgz  .

172.61.143.237(/etc/haproxy/haproxy.cfg)
haproxy -f /etc/haproxy/haproxy.cfg -c
service haproxy reload
/root/kafka_2.13-3.9.0/bin/kafka-topics.sh --list   --bootstrap-server  172.61.143.237:30898
/root/kafka_2.13-3.9.0/bin/kafka-topics.sh --list   --bootstrap-server  10.190.227.110:30898

10.190.227.110 30898/30899/30900

3、镜像
https://docker.aityp.com/
ansible k8s -m shell -a 'ctr -n k8s.io images pull swr.cn-north-4.myhuaweicloud.com/ddn-k8s/docker.io/library/mysql:8.0.34 && ctr -n k8s.io images tag  swr.cn-north-4.myhuaweicloud.com/ddn-k8s/docker.io/library/mysql:8.0.34  docker.io/library/mysql:8.0.34'
kubectl patch deployment flink1-19 -n flink1-19 --patch '{"spec": {"template": {"spec": {"containers": [{"name": "flink","image":"apache/flink:1.19.0"}]}}}}'
kubectl set image deploy image-deployment *=registry.cn-beijing.aliyuncs.com/mrvolleyball/nginx:v2
crictl images ls|grep flink
mvn dependency:copy-dependencies -DoutputDirectory=lib
docker save harbor.feihong.vip/prometheus-data-service:1.0 > monitor.tar
ansible k8s -m copy  -a 'src=/root/software/prometheus-data-service/monitor.tar dest=/tmp/'
ansible k8s -m shell -a 'ctr -n k8s.io image import /tmp/monitor.tar'
