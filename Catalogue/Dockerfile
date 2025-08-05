FROM node:20
WORKDIR /app
COPY *.js package .
COPY *.json .
RUN npm install
ENV MONGO="true" \
    MONGO_URL="mongodb://<MONGODB-SERVER-IPADDRESS>:27017/catalogue"
CMD ["node", "server.js"]