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
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue" \
    REDIS_URL="redis://redis:6379"
WORKDIR /opt/server
COPY --from=builder /opt/server/ /opt/server/
# Copy the built application files from the builder stage
CMD ["node", "server.js"]








# FROM node:20
# WORKDIR /app
# COPY package*.json .
# COPY *.js .
# RUN npm install
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue" \
#     REDIS_URL="redis://redis:6379"
# CMD ["node", "server.js"]
