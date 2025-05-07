FROM golang:latest

#Install and update system dependencies
RUN apt update -y; apt install -y supervisor

#Prepare and setup the working directory
RUN mkdir -p /app
WORKDIR /app
COPY vsnippet .
COPY config/supervisord.conf /etc/supervisord.conf

# Create a non-root user and switch to it
RUN useradd -m appuser
USER appuser

EXPOSE 1337

ENTRYPOINT [ "/usr/bin/supervisord", "-c", "/etc/supervisord.conf" ]
