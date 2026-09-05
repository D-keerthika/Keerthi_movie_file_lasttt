FROM public.ecr.aws/docker/library/python:3.10-alpine
ENV FLASK_RUN_HOST=0.0.0.0
ENV PYTHONPATH=/app

RUN adduser -u 1000 -D app
RUN apk update && \
  apk add \
  pcre \
  pcre-dev \
  build-base \
  gcc \
  linux-headers \
  openssl \
  libffi-dev \
  && pip install --no-cache-dir pipenv gunicorn

WORKDIR /app

COPY Pipfile* /app/
RUN pipenv install --system --skip-lock

COPY . /app/

USER app

EXPOSE 5000

CMD ["gunicorn", "-b", "0.0.0.0:5000", "movies_api:app"]