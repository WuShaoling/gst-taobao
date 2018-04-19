FROM hadoop:base

# add desktop link
RUN mkdir /root/Desktop \
  && cp /usr/share/applications/firefox.desktop /root/Desktop \
  && cp /usr/share/applications/gedit.desktop /root/Desktop
COPY eclipse.desktop /root/Desktop/

# install font
COPY wqy-microhei-lite-0.2.0_beta-8-any.pkg.tar.xz /
RUN tar xpvf /wqy-microhei-lite-0.2.0_beta-8-any.pkg.tar.xz \
 && rm -f /wqy-microhei-lite-0.2.0_beta-8-any.pkg.tar.xz

# set simplify input auto start
COPY fcitx.desktop /root/.config/autostart
