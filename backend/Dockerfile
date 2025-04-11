FROM python:3.12-slim

WORKDIR /app

# Устанавливаем uv
RUN pip install --no-cache-dir uv

# Копируем зависимости
COPY pyproject.toml uv.lock* .

# Устанавливаем зависимости
RUN uv pip install --system --no-cache-dir -r pyproject.toml

# Копируем код
COPY . .

# Переменные окружения
ENV PYTHONPATH=/app
ENV UVICORN_RELOAD=true

CMD ["uv", "run", "app.main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]