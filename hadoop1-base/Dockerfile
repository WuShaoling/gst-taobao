FROM cloudwarelabs/xfce4-pulsar-ide:latest
RUN apt-get update
RUN apt-get install -y gedit \
    && apt-get install -y unzip \
    && apt-get install -y vim

# 安装字体
COPY wqy-microhei-lite-0.2.0_beta-8-any.pkg.tar.xz /
RUN cd /
RUN tar xpvf wqy-microhei-lite-0.2.0_beta-8-any.pkg.tar.xz
# 安装中文输入法
RUN apt-get install -y firefox gedit fcitx fcitx-sunpinyin
COPY fcitx.desktop /root/.config/autostart

COPY gedit.desktop /root/.config/autostart/
