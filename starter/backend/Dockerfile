FROM python:3.10-slim

WORKDIR /app

RUN pip install --no-cache-dir pipenv gunicorn

COPY Pipfile* /app/
RUN pipenv install --system --skip-lock

COPY . /app/

ENV PYTHONPATH=/app
EXPOSE 5000

CMD ["gunicorn", "--bind", "0.0.0.0:5000", "movies_api:app"]