# ----- FETCH REQUIREMENTS ------

FROM python:3.7.0

RUN apt-get update && apt-get install -y gcc make apt-transport-https ca-certificates build-essential

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

ENTRYPOINT ["python"]