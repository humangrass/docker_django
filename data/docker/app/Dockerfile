FROM python:3.11.4

WORKDIR /app
CMD ls

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

COPY ./data/docker/app/requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt

RUN apt-get update && apt-get install -y netcat-traditional libpq-dev
RUN pip install gunicorn


COPY ./data/docker/app/gunicorn.conf.py /app/
#CMD gunicorn project.wsgi:application --config gunicorn.conf.py
CMD gunicorn project.wsgi:application --bind 0.0.0.0:8000
