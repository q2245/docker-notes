# Fedora 44 Docker 安装笔记

## 安装依赖和仓库

```bash
sudo dnf -y install dnf-plugins-core
sudo dnf -y config-manager addrepo --overwrite --from-repofile=https://download.docker.com/linux/fedora/docker-ce.repo
```

## 安装 Docker CE 和 Compose

```bash
sudo dnf -y install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## 启动服务并加入用户组

```bash
sudo systemctl enable --now docker
sudo usermod -aG docker springchang
```

## 配置镜像加速

创建 `/etc/docker/daemon.json`：

```json
{
  "registry-mirrors": ["https://docker.m.daocloud.io"]
}
```

重启服务：

```bash
sudo systemctl restart docker
```

## 验证

```bash
docker --version
docker compose version
docker run --rm hello-world
```

## 注意事项

- 加入 `docker` 组后，需要执行 `newgrp docker` 或注销重新登录才能免 `sudo` 使用。
- 如果官方 Docker Hub 连接超时，可以用上面的 DaoCloud 镜像源。
