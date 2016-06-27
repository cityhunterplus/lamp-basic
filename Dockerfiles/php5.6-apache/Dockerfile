FROM centos:7
MAINTAINER shigeo shigeo@feem.co.jp

# httpd (apache) とPHP5.6 をインストールするためのリポジトリ追加。念のため wget も。
RUN ["yum", "install", "-y", "less", "wget", "httpd", "epel-release"]
RUN ["rpm", "-Uvh", "http://rpms.famillecollet.com/enterprise/remi-release-7.rpm"]

# PHP5.6 をインストール。
RUN ["yum", "-y", "install", "--enablerepo=remi,remi-php56", "php", "php-devel", "php-mbstring", "php-pdo", "php-gd", "php-mysql", "php-mcrypt", "php-xml"]

# あらかじめ用意した httpd.conf、php.ini をコンテナにコピー。
COPY ["./httpd.conf", "/etc/httpd/conf/httpd.conf"]
COPY ["./php.ini", "/etc/php.ini"]

# composer をインストール。composer を使用しない場合は不要。
# 極力最新の状態にしたいのでコンテナ作成時に実行する CMD で実行。
CMD ["curl", "-sS", "https://getcomposer.org/installer", "|", "php"]
# docker centos のイメージには /usr/local がないようなので、ここで作成する。
CMD ["mkdir", "-p", "/usr/local/bin"]
CMD ["mv", "./composer.phar", "/usr/local/bin/composer"]

# httpd を起動するように設定。
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
