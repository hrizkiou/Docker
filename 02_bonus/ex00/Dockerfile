FROM node:7-alpine
RUN mkdir /opt/node
WORKDIR /opt/node
RUN npm init -y
COPY index.js /opt/node
RUN npm install
EXPOSE 8080
CMD ["node", "index.js"]
