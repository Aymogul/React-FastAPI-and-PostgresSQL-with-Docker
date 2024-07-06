# backend/Dockerfile
FROM python:3.11-buster

RUN pip install poetry

COPY . .

RUN poetry install

WORKDIR /api

EXPOSE 8000

CMD ["fastapi", "run", "app/main.py", "--port", "8000"]

    