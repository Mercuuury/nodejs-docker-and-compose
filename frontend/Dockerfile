# Этап 1: Сборка фронтенда
FROM node:16-alpine AS builder

WORKDIR /app

# Копируем package.json и package-lock.json для кэширования зависимостей
COPY package*.json ./

# Устанавливаем зависимости
RUN npm ci

# Копируем исходный код
COPY . .

# Собираем проект
RUN npm run build

# Этап 2: Продакшн образ с nginx
FROM nginx:latest

# Копируем собранный проект из первого этапа
COPY --from=builder /app/build /usr/share/nginx/html

# Копируем конфигурацию nginx
COPY nginx/conf.d/default.conf /etc/nginx/conf.d/default.conf

# Пробрасываем порт
EXPOSE 80

# Запускаем nginx (выполняется команда по умолчанию из образа nginx)