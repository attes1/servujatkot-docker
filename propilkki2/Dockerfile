FROM ubuntu:latest
RUN apt-get update
RUN apt-get install -y wget nano gnupg apt-utils
RUN wget -O - http://procyon.ddns.net:8080/propilkki_pub.gpg.key | apt-key add -
RUN echo "deb http://procyon.ddns.net:8080/repos/apt/ubuntu noble main" | tee -a /etc/apt/sources.list
RUN apt-get update
RUN apt-get install pp2host
COPY autohost.ini /etc/pp2host/static/autohost.ini
COPY pp2host.conf /etc/pp2host/pp2host.conf
ARG ORGA
ARG SERVER_NAME
ARG ADMIN_PW
ARG HOST_PW
ARG PILKKI_PW
ENV ORGA $ORGA
ENV SERVER_NAME $SERVER_NAME
ENV ADMIN_PW $ADMIN_PW
ENV HOST_PW $HOST_PW
ENV PILKKI_PW $PILKKI_PW
RUN sed -i "s/\$ORGA/$ORGA/g" /etc/pp2host/pp2host.conf
RUN sed -i "s/\$SERVER_NAME/$SERVER_NAME/g" /etc/pp2host/pp2host.conf
RUN sed -i "s/\$ADMIN_PW/$ADMIN_PW/g" /etc/pp2host/pp2host.conf
RUN sed -i "s/\$HOST_PW/$HOST_PW/g" /etc/pp2host/pp2host.conf
RUN sed -i "s/\$PILKKI_PW/$PILKKI_PW/g" /etc/pp2host/pp2host.conf
CMD ["sh", "-c", "service pp2host start && tail -f /dev/null"]
