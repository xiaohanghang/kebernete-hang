# Kubernetes架构

Kubernetes主要由以下几个核心组件组成：

1. etcd保存了整个集群的状态；
2. apiserver提供了资源操作的唯一入口，并提供认证、授权、访问控制、API注册和发现等机制；
3. controller manager负责维护集群的状态，比如故障检测、自动扩展、滚动更新等；
4. scheduler负责资源的调度，按照预定的调度策略将Pod调度到相应的机器上；

5. kubelet负责维护容器的生命周期，同时也负责Volume（CVI） 和网络（CNI） 的管理；

6. Container runtime负责镜像管理以及Pod和容器的真正运行（CRI） ；

7. kube-proxy负责为Service提供cluster内部的服务发现和负载均衡；![](/assets/import.png)![](/assets/import1.png)

# pod基本概念

Pod是一组紧密关联的容器集合，它们共享IPC、Network和UTC namespace，是Kubernetes调度的基本单位。Pod的设计理念是支持多个容器在一个Pod中共享网络和文件系统，可以通过进程间通信和文件共享这种简单高效的方式组合完成服务。

