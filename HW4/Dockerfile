FROM alpine:latest
FROM python:3
RUN apt-get update && \
	apt-get install -y\
	curl \
	wget \
	&& rm -rf /var/lib/apt/lists/*
WORKDIR /app
COPY . .
ADD task.py /
CMD [ "python", "./task.py" ]