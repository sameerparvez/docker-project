FROM python:3
WORKDIR /opt/server
COPY requirements.txt .
COPY *.py .
COPY payment.ini .
RUN pip install -r requirements.txt
CMD ["uwsgi", "--ini", "payment.ini"]
ENV CART_HOST="cart" /
    CART_PORT="8080" /
    USER_HOST="user" /
    USER_PORT="8080" /
    AMQP_HOST="rabbitmq" /
    AMQP_USER="roboshop" /
    AMQP_PASSWORD="roboshop123" /
    