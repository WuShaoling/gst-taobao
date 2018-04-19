FROM cloudwarelabs/xfce4-pulsar-ide:latest
RUN apt-get update \
    && apt-get install -y gedit \
    && apt-get install -y unzip \
    && apt-get install -y vim \
    && apt-get install -y firefox \
    && apt-get install -y fcitx fcitx-sunpinyin

# 安装字体
COPY wqy-microhei-lite-0.2.0_beta-8-any.pkg.tar.xz /
RUN tar xpvf /wqy-microhei-lite-0.2.0_beta-8-any.pkg.tar.xz \
 && rm -f /wqy-microhei-lite-0.2.0_beta-8-any.pkg.tar.xz

# 设置输入法自动启动
COPY fcitx.desktop /root/.config/autostart
