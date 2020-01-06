FROM httpd:2.4
RUN rm /usr/local/apache2/htdocs/index.html
RUN mkdir /usr/local/apache2/htdocs/login
COPY login/* /usr/local/apache2/htdocs/login/
WORKDIR /usr/local/apache2/htdocs/login/
