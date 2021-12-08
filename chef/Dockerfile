FROM centos:7
MAINTAINER raj verma
ENV APP /app
WORKDIR $APP
RUN yum update -y && yum -y install wget
RUN wget https://packages.chef.io/files/stable/chef-server/14.9.23/el/7/chef-server-core-14.9.23-1.el7.x86_64.rpm
RUN rpm -Uvh chef-server-core-14.9.23-1.el7.x86_64.rpm
ADD . $APP
CMD ["run_server"]
EXPOSE 443
