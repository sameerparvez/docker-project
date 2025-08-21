FROM maven AS builder
# Use a multi-stage build to reduce the final image size
WORKDIR /opt/server
COPY pom.xml .
# Copy the pom.xml file first to leverage Docker cache
COPY src /opt/server/src
RUN mvn clean package


FROM eclipse-temurin:21-jre-alpine
# Use a smaller base image for the final build
EXPOSE 8080
WORKDIR /opt/server
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
ENV CART_ENDPOINT="cart:8080"/
    DB_HOST="mysql"
COPY --from=builder /opt/server/target/shipping-*.jar /opt/server/shipping.jar
# Copy the built application files from the builder stage
USER roboshop
CMD ["java", "-jar", "shipping.jar"]
     










# FROM maven
# WORKDIR /opt/server
# COPY src /opt/server/src
# COPY pom.xml .
# RUN mvn clean package
# RUN mv opt/server/target/shipping-1.0.jar /app/shipping.jar
# ENV CART_ENDPOINT="cart:8080"/
#     DB_HOST="mysql"
# CMD ["java", "-jar", "shipping.jar"]
     