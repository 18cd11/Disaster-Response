FROM ubuntu:22.04
MAINTAINER juanable.wang@gmail.com

RUN apt-get update -y
RUN apt-get install python3-pip -y
RUN apt-get install gunicorn3 -y

# Copy requirements to new dir app
COPY requirements.txt requirements.txt

COPY flaskapp /opt/

RUN pip install -r requirements.txt
# Install extral packages
#RUN python -c "import nltk; nltk.download('stopwords'); nltk.download('wordnet');nltk.download('punkt')"
RUN python3 -m nltk.downloader stopwords
RUN python3 -m nltk.downloader punkt
RUN python3 -m nltk.downloader wordnet

WORKDIR /opt

CMD ['gunicorn3', '-b', '0.0.0.0:8000', 'app:app','--workers=5']