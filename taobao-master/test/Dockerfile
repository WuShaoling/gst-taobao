FROM cloudwarelabs/xfce4-pulsar-ide

ARG DEBIAN_FRONTEND=noninteractive

# Install MySQL
RUN sudo apt-get update \
  && echo mysql-server mysql-server/root_password password 123456 | debconf-set-selections \
  && echo mysql-server mysql-server/root_password_again password 123456 | debconf-set-selections \
  && sudo apt-get install -y mysql-server-5.6
