FROM python:3.9.7 as backend

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8

# Add buster Postgres repo. This is necessary to install postgresql-client-12
RUN wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
RUN echo "deb http://apt.postgresql.org/pub/repos/apt/ buster-pgdg main" | tee  /etc/apt/sources.list.d/pgdg.list

RUN apt-get update && apt-get install -y \
    postgresql-client-12 \
    libpq-dev \
    build-essential \
    libcairo2-dev \
    libpango1.0-dev \
    libjpeg-dev \
    libgif-dev \
    librsvg2-dev \
    gdal-bin \
    g++

RUN pip install pip

WORKDIR /opt/code

COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt

COPY . ./