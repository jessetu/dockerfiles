FROM maven:3.8.1-jdk-11-slim

# 指定构建过程中的工作目录
WORKDIR /app

# 安装依赖包，如需其他依赖包，请到alpine依赖包管理(https://pkgs.alpinelinux.org/packages?name=php8*imagick*&branch=v3.13)查找。
# 选用国内镜像源以提高下载速度
RUN sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list \
    # && chmod 777 /root/.ssh \
    && apt-get update \
    && apt-get install -y git \
    && apt-get install -y openssh-server \
    && /etc/init.d/ssh restart \
    && rm -rf /var/lib/apt/lists/*

# 手动构建自己的项目
# 下载项目依赖包，加快每次构建的速度。

# 复制当前目录下的.ssh相关文件
COPY .ssh /root/.ssh

RUN chmod 755 /root/.ssh 
RUN git clone -b git@github.com:xxxxx/project-app.git project-app \
    && cd project-app \
    && mvn clean package -Dmaven.test.skip=true && mvn clean

CMD echo "success--------------ok"
