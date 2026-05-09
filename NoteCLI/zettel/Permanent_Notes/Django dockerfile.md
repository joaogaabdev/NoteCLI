
``` dockerfile
FROM python:3.9-alpine3.13

COPY ./requirements.txt /tmp/requirements.txt
COPY ./app /app
WORKDIR /app
EXPOSE 8000

RUN python -m venv /py && \
    /py/bin/pip install --upgrade pip && \
    apk add --update --no-cache postgresql-client && \
    apk add --update --no-cache --virtual .tmp-build-deps \
        build-base postgresql-dev musl-dev && \
    /py/bin/pip install -r /tmp/requirements.txt && \
    rm -rf /tmp && \
    apk del .tmp-build-deps && \
    adduser \
        --disabled-password \
        --no-create-home \
        django-user
ENV PATH="/py/bin:$PATH"

USER django-user
```

``` docker-compose

version: '3.9'
services:
  db:
    image: postgres:13-alpine
    volumes:
      - django_postgres_data:/var/lib/postgresql/data/
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=postgres
    ports:
      - "5432:5432"
  app:
    build: .
    context: .
    ports:
      - "8000:8000"
    volumes:
      - ./app: /app
    command: >
      sh -c "python manage.py migrate &&
             python manage.py runserver 0.0.0.0:8000"
    environment:
      - DB_HOST=db
      - DB_NAME=postgres
      - DB_USER=postgres
      - DB_PASSWORD=postgres
    depends_on:
        - db
volumes:
  django_postgres_data:
```