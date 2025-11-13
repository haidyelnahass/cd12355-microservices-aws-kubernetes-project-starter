FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .

RUN apt update -y && \
    apt install -y build-essential libpq-dev && \
    pip install --upgrade pip setuptools wheel && \
    pip install --no-cache-dir -r requirements.txt && \
    apt clean && rm -rf /var/lib/apt/lists/*

COPY . .

ENV DB_USERNAME=myuser
ENV DB_PASSWORD=mypassword
ENV DB_HOST=postgresql-service
ENV DB_PORT=5433
ENV DB_NAME=mydatabase

CMD ["python", "app.py"]