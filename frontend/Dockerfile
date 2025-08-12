FROM Nginx
RUN rm -f /etc/nginx/nginx.conf
RUN rm -rf /usr/share/nginx/html/index.html
ADD nginx.conf /etc/nginx/nginx.conf
ADD static/* /usr/share/nginx/html/