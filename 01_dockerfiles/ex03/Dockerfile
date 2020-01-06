FROM ubuntu
EXPOSE 80 443 2020
RUN apt update -y && apt upgrade -y && apt install -y curl openssh-server postfix ca-certificates tzdata
RUN curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash
RUN apt install -y gitlab-ce && rm -rf /var/lib/apt/lists/*
RUN mkdir -p /etc/gitlab/ssl && chmod 700 /etc/gitlab/ssl
RUN openssl req -x509 -nodes -days 365 -newkey rsa:4096 -keyout "/etc/gitlab/ssl/server.key" -out "/etc/gitlab/ssl/server.crt" -subj "/C=MA/ST=Khouribga/L=KHOURIBGA/O=1337/OU=IT/CN=10.12.3.3"
RUN sed -i 's/http:\/\/gitlab.example.com/https:\/\/10.12.3.3/' /etc/gitlab/gitlab.rb
RUN echo "nginx['enable'] = true" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['redirect_http_to_https'] = true" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['ssl_certificate'] = \"/etc/gitlab/ssl/server.crt\"" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['ssl_certificate_key'] = \"/etc/gitlab/ssl/server.key\"" >> /etc/gitlab/gitlab.rb
RUN echo "gitlab_rails['gitlab_shell_ssh_port'] = 2020" >> /etc/gitlab/gitlab.rb
RUN echo "Port 2020" >> /etc/ssh/sshd_config
ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && service ssh restart && gitlab-ctl tail
