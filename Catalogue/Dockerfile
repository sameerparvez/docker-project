FROM node:20-alpine3.21 AS Builder
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
    MONGO_URL="mongodb://mongodb:27017/catalogue"
WORKDIR /opt/server
COPY --from=Builder /opt/server/ /opt/server/
# Copy the built application files from the builder stage
CMD ["node", "server.js"]
















# FROM node:20-alpine3.21
# #instead of using node:20 using above one to reduce the size of the image
# WORKDIR /opt/server
# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
# USER roboshop
# COPY *.js .
# COPY *.json .
# RUN npm install
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node", "server.js"]