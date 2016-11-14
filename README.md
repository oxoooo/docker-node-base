基础 NodeJS Docker 镜像
==========

## 约定

- App 运行于 `$APP_HOME`（`/var/app`）目录
- App 监听 `$PORT`（`8000`）端口
- 所有静态资源编译在 `$APP_HOME/dist` 目录，对外访问路径为 `/assets`
- App 通过 `npm start` 命令启动

## 示例

```Dockerfile
FROM registry-internal.cn-hangzhou.aliyuncs.com/aja/base-node:1.0
MAINTAINER 你的名字 "你的邮箱"

WORKDIR $APP_HOME

ADD package.json $APP_HOME
RUN npm install

ADD . $APP_HOME

ENV NODE_ENV=production
RUN npm run build

CMD [ "./start.sh" ]
```
