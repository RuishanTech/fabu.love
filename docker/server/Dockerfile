FROM node:8.14

# 安装运行环境
RUN apt-get update && \
    apt-get install -y build-essential && \
    apt-get install -y python

# 安装依赖库
RUN npm install -g pm2 babel-cli node-gyp

# 设置目录
RUN mkdir -p /opt/data /opt/server /opt/logs

# 增加启动脚本
ADD docker/server/docker-entrypoint.sh /opt/server/
RUN chmod +x /opt/server/docker-entrypoint.sh

# 增加server
WORKDIR /opt/server
ADD server /opt/server
RUN npm install

EXPOSE 9898

ENTRYPOINT ["/opt/server/docker-entrypoint.sh"]
