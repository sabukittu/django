FROM python:3.8.2-alpine

RUN apk update && apk add --no-cache --virtual .build-deps gcc libc-dev \
    && pip install Django==2.1.5 gunicorn \
    && apk del .build-deps gcc libc-dev

COPY ./login_logout /login_logout

WORKDIR /login_logout/

EXPOSE 8000

CMD ["gunicorn", "login_logout.wsgi:application", "--bind", "myapp:8000"]
