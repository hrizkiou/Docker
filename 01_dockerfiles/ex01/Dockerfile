FROM archlinux
MAINTAINER hrizkiou
RUN pacman -Syy --noconfirm && pacman -S wget tar --noconfirm && pacman -Scc --noconfirm
RUN wget https://files.teamspeak-services.com/releases/server/3.10.2/teamspeak3-server_linux_amd64-3.10.2.tar.bz2
RUN tar -xvf teamspeak3-server_linux_amd64-3.10.2.tar.bz2
RUN mv teamspeak3-server_linux_amd64 teamspeak3
RUN rm -rf teamspeak3-server_linux_amd64-3.10.2.tar.bz2
WORKDIR teamspeak3
RUN touch .ts3server_license_accepted
EXPOSE 9987/udp 10011 30033
ENTRYPOINT ["./ts3server"]
