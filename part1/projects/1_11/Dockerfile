FROM ubuntu:16.04

WORKDIR /app

COPY . .

RUN apt-get update && apt-get install -y curl

RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
RUN apt install -y nodejs
RUN npm install

RUN node -v && npm -v

EXPOSE 8000

CMD ["npm", "start"]
