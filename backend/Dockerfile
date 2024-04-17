# Build stage for FastAPI backend
FROM python:3.9-slim as base
RUN apt-get update && apt-get install -y --no-install-recommends \
    gcc \
    libc6-dev \
    libkrb5-dev \
    && rm -rf /var/lib/apt/lists/*
FROM base as python-build
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .

EXPOSE 3001

# Run the command to start uvicorn
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "3001"]
