# [快速自建一套镜像加速器，可拉取所有墙外镜像](https://mp.weixin.qq.com/s/lnztLgCnephk1b1muhKsNw)
使用Github Action将Docker镜像转存到阿里云私有仓库，彻底解决在国内Docker镜像无法拉取的问题。

## 配置阿里云镜像仓库
 - 登录阿里云后，进入容器镜像服务 https://cr.console.aliyun.com/cn-hangzhou/instances
 - 创建个人实例
 - 创建个人实例（免费），创建一个命名空间（后面会用于环境变量ALIYUN_NAME_SPACE）
 - 查看访问凭证

## 创建GitHub仓库并设置
### 创建GitHub仓库
### 启动Action
 进入您自己的项目，点击Action，启用Github Action工作流功能
新建你的workflows，docker.yml
### 配置环境变量
进入Settings->Secret and variables->Actions->New Repository secret
ALIYUN_NAME_SPACE=你的镜像仓库的命名空间，我建议新建一个新的，公开的。
ALIYUN_REGISTRY=registry.cn-镜像仓库的地区.aliyuncs.com
ALIYUN_REGISTRY_USER=你的用户名
ALIYUN_REGISTRY_PASSWORD=输入自己设置的密码

## 配置镜像清单
根目录创建，添加你想要的镜像
可以加tag，也可以不用(默认latest)
可添加 --platform=xxxxx 的参数指定镜像架构
可使用 k8s.gcr.io/kube-state-metrics/kube-state-metrics 格式指定私库
可使用注释
