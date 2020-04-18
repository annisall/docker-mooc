FROM ubuntu:16.04

WORKDIR /thisfolder
COPY start.sh .

# We could do this before copying, locally, but thought that this would make sure it's executable
RUN chmod +x start.sh

RUN apt-get update && apt-get install -y curl

CMD ["./start.sh"]
