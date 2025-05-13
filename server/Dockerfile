FROM python:3.11-slim

# Install Poetry
RUN pip install poetry

WORKDIR /app

# Copy only dependency files first
COPY pyproject.toml poetry.lock ./

# Install dependencies
RUN poetry config virtualenvs.create false \
  && poetry install --no-root

# Copy rest of the application
COPY . .

# Port
EXPOSE 8000

CMD ["gunicorn", "server.wsgi:application", "--bind", "0.0.0.0:8000"]

