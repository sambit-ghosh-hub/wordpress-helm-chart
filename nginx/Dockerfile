FROM ubuntu

#install openresty build dependencies
RUN apt-get install libpcre3-dev libssl-dev perl make build-essential curl

#Download openresty source tar
RUN curl https://openresty.org/download/openresty-1.25.3.1.tar.gz -o openresty-1.25.3.1.tar.gz

#Build openresty
RUN tar -xzvf openresty-1.25.3.1.tar.gz; \
    cd openresty-1.25.3.1; \
    ./configure --prefix=/opt/openresty \
                --with-pcre-jit \
                --with-ipv6 \
                --without-http_redis2_module \
                --with-http_iconv_module \
                --with-http_postgres_module \
                -j8; \
    make -j8; \
    make install;

RUN export PATH=/opt/openresty/bin:$PATH

# copy proxypass config to docker
COPY . .

# run nginx server
CMD ["/opt/openresty/nginx/sbin/nginx","-p","`pwd`/","-c", "nginx.conf"]

EXPOSE 80
