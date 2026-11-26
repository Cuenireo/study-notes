# Docker：ARG 和 ENV 的区别

```dockerfile
ARG NODE_VERSION=20        # 构建时参数
FROM node:${NODE_VERSION}

ENV APP_ENV=production     # 运行时环境变量，容器里能读到
RUN echo "构建用 $NODE_VERSION"
```

```bash
docker build --build-arg NODE_VERSION=18 -t myapp .
```

- `ARG` 只在构建时有效，镜像跑起来就没了；`ENV` 会留在镜像里，容器能读到。
- 密钥别用 `ARG` 传，会留在镜像历史里，`docker history` 翻得出来。
- 构建时想用密钥：用 BuildKit 的 `--secret`，不进镜像层。
