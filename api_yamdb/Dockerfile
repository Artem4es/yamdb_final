FROM python:3.7-slim

WORKDIR /app

COPY api_yamdb/requirements.txt .

RUN pip install -r requirements.txt --no-cache-dir

COPY /api_yamdb .

CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ]

<<<<<<< HEAD
RUN python manage.py collectstatic --noinput
=======
RUN python3 manage.py collectstatic --noinput
>>>>>>> 49e3a07c6c664610a136d1aad75f9b091246f091
