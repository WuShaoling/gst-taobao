FROM cloudwarelabs/xfce4-pulsar-ide:latest
RUN apt-get update
RUN apt-get install -y gedit \
    && apt-get install -y unzip \
    && apt-get install -y vim
COPY gedit.desktop /root/.config/autostart/
