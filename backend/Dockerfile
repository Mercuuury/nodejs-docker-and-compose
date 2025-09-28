# Этап 1: Сборка проекта
FROM node:16-alpine AS builder

WORKDIR /app

# Копируем package.json и package-lock.json для кэширования зависимостей
COPY package*.json ./

# Устанавливаем все зависимости (включая dev)
RUN npm ci

# Копируем исходный код
COPY . .

# Собираем проект
RUN npm run build

# Этап 2: Продакшн образ
FROM node:16-alpine AS production

WORKDIR /app

# Устанавливаем pm2 глобально
RUN npm install -g pm2

# Копируем package.json и package-lock.json
COPY package*.json ./

# Устанавливаем только production зависимости
RUN npm ci --omit=dev && npm cache clean --force

# Копируем собранный проект из первого этапа
COPY --from=builder /app/dist ./dist

# Копируем ecosystem.config.js для pm2
COPY ecosystem.config.js ./

# Пробрасываем порт
EXPOSE 3000

# Запускаем приложение через pm2
CMD ["pm2-runtime", "start", "ecosystem.config.js"]