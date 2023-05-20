FROM ubuntu:20.04
RUN apt-get update && apt-get install -y python3.8 python3-pip
EXPOSE 5000
WORKDIR app/
COPY . .
RUN pip3 install -r requirements.txt
CMD ["python3", "app.py"]

