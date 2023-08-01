FROM python:3.9-alpine3.16

# Add required libraries and build dependencies, install parsedmarc, and remove build dependencies
RUN apk add --update --no-cache libxml2-dev libxslt-dev \
    && apk add --update --no-cache --virtual .build_deps build-base \
    && pip install --no-cache-dir parsedmarc \
    && apk del .build_deps

# Copy the parsedmarc configuration file
COPY parsedmarc.ini /