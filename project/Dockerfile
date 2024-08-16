# Используем базовый образ Python
FROM python:3.12.5-bullseye

# Устанавливаем curl и другие необходимые пакеты для установки Poetry
RUN apt-get update && apt-get install -y curl && apt-get clean

# Устанавливаем Poetry
RUN curl -sSL https://install.python-poetry.org | python3 -

# Добавляем Poetry в PATH
ENV PATH="/root/.local/bin:$PATH"

# Устанавливаем рабочую директорию
WORKDIR /app

# Копируем файлы с описанием зависимостей
COPY pyproject.toml ./

# Устанавливаем зависимости через Poetry
RUN poetry install --no-root --no-dev

# Копируем остальные файлы проекта
COPY . .

# Указываем команду для запуска приложения
CMD ["bash"]
