1. 卸载旧版本（如果有）
如果你之前安装过 Docker，请先卸载旧版本：

bash
复制
sudo apt remove docker docker-engine docker.io containerd runc
2. 更新系统包
确保系统包是最新的：

bash
复制
sudo apt update
sudo apt upgrade -y
3. 安装依赖工具
安装必要的工具以允许 apt 通过 HTTPS 使用仓库：

bash
复制
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
4. 添加 Docker 官方 GPG 密钥
添加 Docker 的官方 GPG 密钥以验证软件包的真实性：

bash
复制
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
5. 添加 Docker 仓库
将 Docker 的稳定版仓库添加到 APT 源中：

bash
复制
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
6. 更新 APT 包索引
更新 APT 包索引以包含 Docker 仓库：

bash
复制
sudo apt update
7. 安装 Docker
安装 Docker 引擎、CLI 和 Containerd：

bash
复制
sudo apt install -y docker-ce docker-ce-cli containerd.io
8. 启动并启用 Docker 服务
启动 Docker 服务并设置为开机自启：

bash
复制
sudo systemctl start docker
sudo systemctl enable docker
9. 验证安装
检查 Docker 是否安装成功：

bash
复制
sudo docker --version
运行一个测试容器：

bash
复制
sudo docker run hello-world
如果看到 "Hello from Docker!" 的消息，说明 Docker 安装成功。

10. 配置非 root 用户使用 Docker（可选）
默认情况下，Docker 需要 sudo 权限。如果你希望非 root 用户也能使用 Docker，可以将用户添加到 docker 组：

bash
复制
sudo usermod -aG docker $USER
然后注销并重新登录，或者重启系统。

11. 配置 Docker 镜像加速（可选）
如果你在国内，可以配置 Docker 镜像加速以提升拉取镜像的速度。编辑 Docker 配置文件：

bash
复制
sudo nano /etc/docker/daemon.json
添加以下内容（以阿里云镜像加速为例）：

json
复制
{
  "registry-mirrors": ["https://<your-mirror-id>.mirror.aliyuncs.com"]
}
保存后重启 Docker 服务：

bash
复制
sudo systemctl restart docker
总结
通过以上步骤，你可以在 Ubuntu 上成功安装 Docker，并配置好基本环境。接下来，你可以开始使用 Docker 来管理和运行容器了！