FROM node:20-alpine3.21
WORKDIR /opt/server
COPY *.js .
COPY *.json .
RUN npm install
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD ["node", "server.js"]