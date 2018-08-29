# https://github.com/docker/for-mac/issues/770
# docker run -d -v /var/run/docker.sock:/var/run/docker.sock -p 127.0.0.1:1234:1234 bobrik/socat TCP-LISTEN:1234,fork UNIX-CONNECT:/var/run/docker.sock
FROM centos:7.5.1804
LABEL maintainer="mstewart@riotgames.com"
RUN yum -y install socat && \
    yum clean all
VOLUME /var/run/docker.sock
# docker tcp port
EXPOSE 2375
ENTRYPOINT ["socat", "TCP-LISTEN:2375,reuseaddr,fork","UNIX-CLIENT:/var/run/docker.sock"]