FROM python:3.12

WORKDIR /app

# Устанавливаем gunicorn
RUN pip install gunicorn==23.0.0

COPY requirements.txt .

# Устанавливаем зависимости
RUN pip install -r requirements.txt --no-cache-dir

COPY . .

# Собираем статику
RUN python manage.py collectstatic --noinput

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "kittygram_backend.wsgi"]
