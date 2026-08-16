# Grab the latest alpine images
FROM python:3.11-alpine

# Install python and pip
# hadolint ignore=DL3018

LABEL maintainer="Gastech"

RUN apk add --no-cache --update bash

COPY ./webapp/requirements.txt /tmp/requirements.txt


# Mettre à jour pip/setuptools/wheel (versions les plus récentes = correctifs de
# sécurité) puis installer les dépendances de l'app, en une seule couche
# hadolint ignore=DL3013
RUN pip3 install --no-cache-dir --upgrade pip setuptools wheel && \
    pip3 install --no-cache-dir -q -r /tmp/requirements.txt

# Add our code
COPY ./webapp /opt/webapp/
WORKDIR /opt/webapp

# Run the image as a non-root user
RUN adduser -D -u 1000 myuser
USER 1000

# Run the app
CMD ["gunicorn", "--bind", "0.0.0.0:5000", "wsgi:application"]