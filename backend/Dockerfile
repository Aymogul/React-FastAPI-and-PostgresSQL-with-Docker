# Use an official Python runtime as a parent image
FROM python:3.10-slim

# Set the working directory in the container
WORKDIR /app

# Install curl
RUN apt-get update && apt-get install -y curl

# Install Poetry
RUN curl -sSL https://install.python-poetry.org | python3 -

# Add Poetry to PATH
ENV PATH="/root/.local/bin:$PATH"

# # Copy the pyproject.toml and poetry.lock files
# COPY pyproject.toml poetry.lock ./

# Set environment variables for Poetry
ENV POETRY_HOME="/opt/poetry" \
    PYSETUP_PATH="/app" \
    PIP_NO_CACHE_DIR=off \
    POETRY_VIRTUALENVS_PATH="/app/.venv"

# Copy only the dependencies definition files to leverage caching
COPY pyproject.toml poetry.lock ./

# Disable Poetry's virtual environment creation
RUN poetry config virtualenvs.create false


# Install dependencies
RUN poetry install --no-root

# Copy the rest of the application code into the container
COPY . .

# # Set PYTHONPATH to include the app directory
# ENV PYTHONPATH=/app

# Expose the port that the app runs on
EXPOSE 8000

# Command to run the backend server
CMD ["poetry", "run", "uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]
    