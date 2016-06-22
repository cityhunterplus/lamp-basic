FROM centos:7
MAINTAINER shigeo shigeo@feem.co.jp
RUN ["yum", "install", "-y", "wget", "httpd", "epel-release"]
RUN ["rpm", "-Uvh", "http://rpms.famillecollet.com/enterprise/remi-release-7.rpm"]
RUN ["yum", "-y", "install", "--enablerepo=remi,remi-php56", "php", "php-devel", "php-mbstring", "php-pdo", "php-gd", "php-mysql", "php-mcrypt", "php-xml"]
COPY ["./httpd.conf", "/etc/httpd/conf/httpd.conf"]
COPY ["./php.ini", "/etc/php.ini"]
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
