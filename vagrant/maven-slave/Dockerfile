FROM maven:alpine
#    apk upgrade && \

RUN apk update &&\
    apk add dropbear sudo openssh-client &&\
    rm -rf /var/cache/apk/*
RUN mkdir /etc/dropbear
RUN touch /var/log/lastlog
COPY docker-entrypoint.sh /
ENTRYPOINT ["/docker-entrypoint.sh"]
RUN dropbearkey -t rsa -f /etc/dropbear/dropbear_rsa_host_key
EXPOSE 22
#CMD ["dropbear", "-RFEmwg", "-p", "22"]
CMD ["dropbear", "-RFEm", "-p", "22"]

#FROM maven:alpine

USER root
# install ssh
#RUN apk --update add openssh \
#  && rm -rf /var/cache/apk/*
#RUN apk --update add openssh \
#  && sed -i s/#PermitRootLogin.*/PermitRootLogin\ yes/ /etc/ssh/sshd_config \
#  && echo "root:j3nk1n5Rul35" | chpasswd \
#  && rm -rf /var/cache/apk/*
#RUN apk --update add openssh \
#  && echo "root:j3nk1n5Rul35" | chpasswd \
#  && rm -rf /var/cache/apk/*
#RUN adduser -D jenkins
#RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

#USER jenkins
  
#CMD ["/usr/sbin/sshd", "-D"]
