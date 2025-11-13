FROM public.ecr.aws/sam/build-python3.11:latest

WORKDIR /app

COPY requirements.txt .

RUN yum update -y && \
    yum install -y gcc gcc-c++ postgresql-devel make && \
    pip install --upgrade pip setuptools wheel && \
    pip install --no-cache-dir -r requirements.txt && \
    yum clean all

COPY . .

ENV DB_USERNAME=myuser
ENV DB_PASSWORD=mypassword
ENV DB_HOST=postgresql-service
ENV DB_PORT=5433
ENV DB_NAME=mydatabase

CMD ["python", "app.py"]
