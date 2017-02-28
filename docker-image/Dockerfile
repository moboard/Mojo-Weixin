FROM perl:5.22
MAINTAINER sjdy521 <sjdy521@163.com>
WORKDIR /root
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update && apt-get install -y unzip
RUN cpanm Encode::Locale IO::Socket::SSL Mojolicious
RUN wget -q https://github.com/sjdy521/Mojo-Weixin/archive/master.zip -OMojo-Weixin.zip \
    && unzip -qo Mojo-Weixin.zip \
    && cd Mojo-Weixin-master \
    && cpanm . \
    && cd .. \
    && rm -rf Mojo-Weixin-master Mojo-Weixin.zip
COPY Mojo-Wx.pl Mojo-Wx.pl
CMD ["perl","Mojo-Wx.pl"]
