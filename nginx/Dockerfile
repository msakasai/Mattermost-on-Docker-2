FROM nginx

RUN apt -y update
RUN apt -y install vim wget curl less procps net-tools sudo make cmake gcc g++ zip gzip unzip tar
RUN apt -y install git

COPY mattermost /etc/nginx/conf.d/default.conf

EXPOSE 80
