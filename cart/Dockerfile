FROM node:20-alpine3.21 AS builder
# Use a multi-stage build to reduce the final image size
WORKDIR /opt/server
COPY *.js .
COPY *.json .
RUN npm install

FROM node:20-alpine3.21
# Use a smaller base image for the final build
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
USER roboshop
ENV REDIS_HOST="redis"/
    CATALOGUE_HOST="catalogue" 
WORKDIR /opt/server
COPY --from=builder /opt/server/ /opt/server/
# Copy the built application files from the builder stage
CMD ["node", "server.js"]







# FROM node:20
# WORKDIR /app
# COPY *.js package .
# COPY *.json .
# RUN npm install
# ENV REDIS_HOST="<REDIS-SERVER-IP"/
#     CATALOGUE_HOST="<CATALOGUE-SERVER-IP" 
# CMD ["node", "server.js"]