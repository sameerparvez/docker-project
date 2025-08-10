FROM node:20
WORKDIR /app
COPY *.js package .
COPY *.json .
RUN npm install
ENV REDIS_HOST="<REDIS-SERVER-IP"/
    CATALOGUE_HOST="<CATALOGUE-SERVER-IP" 
CMD ["node", "server.js"]