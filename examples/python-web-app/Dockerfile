FROM ubuntu:latest

WORKDIR /app

ENV DEBIAN_FRONTEND=noninteractive


COPY requirements.txt /app
COPY devops /app

RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

#WORKDIR /app

#COPY requirements.txt .

RUN python3 -m venv /app/venv && \
    /app/venv/bin/pip install --no-cache-dir -r requirements.txt && \
    cd devops
#COPY devops/app .

ENV PATH ="/app/venv/bin:$PATH"
   
#cd devops

EXPOSE 8000
ENTRYPOINT ["python"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]



