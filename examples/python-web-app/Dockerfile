FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt /app
COPY devops /app

RUN pip install --upgrade pip && \
    pip install -r requirements.txt

ENTRYPOINT ["python"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]

