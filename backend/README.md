# КупиПодариДай — Backend API

[![Node.js](https://img.shields.io/badge/Node.js-18.x-green)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-4.3.x-blue)](https://www.typescriptlang.org/)
[![NestJS](https://img.shields.io/badge/NestJS-9.x-red)](https://nestjs.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-13+-blue)](https://www.postgresql.org/)
[![TypeORM](https://img.shields.io/badge/TypeORM-0.3.x-lightgrey)](https://typeorm.io/)

Сервис вишлистов **КупиПодариДай**. Позволяет пользователям делиться списками желаемых подарков и скидываться на них. Каждый пользователь может создать собственный список подарков, просматривать чужие и участвовать в их покупке, указывая сумму, которую он готов внести.

---

## 🚀 Установка и запуск

1. Клонируйте репозиторий:

```bash
git clone https://github.com/Mercuuury/kupipodariday-backend.git
cd kupidopodaridai-backend
```

2. Установите зависимости:

```bash
npm install
```

3. Настройте переменные окружения (.env) по примеру .env.example

4. Запуск в режиме разработки:

```bash
npm run start:dev
```

## 📦 Скрипты

- Dev-сервер с hot-reload: `npm run start:dev`
- Production-сборка и запуск:
  ```bash
  npm run build
  npm start
  ```
- Очистка и сборка проекта: `npm run prebuild && npm run build`
- Линтинг и автофиксы: `npm run lint`
- Форматирование кода: `npm run format`

## 📘 Маршруты API

### 🔐 Аутентификация

- `POST /signup` — регистрация
- `POST /signin` — вход в систему

### 👤 Пользователи

- `GET /users/me` — получить свой профиль
- `PATCH /users/me` — обновить свой профиль
- `GET /users/me/wishes` — получить свои подарки
- `GET /users/:username` — получить профиль по username
- `GET /users/:username/wishes` — получить подарки по username
- `POST /users/find` — поиск пользователей по email/username

### 🎁 Подарки (желания)

- `POST /wishes` — создать подарок
- `GET /wishes/last` — последние добавленные подарки
- `GET /wishes/top` — популярные подарки
- `GET /wishes/:id` — получить подарок по ID
- `PATCH /wishes/:id` — редактировать подарок
- `DELETE /wishes/:id` — удалить подарок
- `POST /wishes/:id/copy` — скопировать подарок к себе

### 📋 Вишлисты

- `GET /wishlists` — получить все вишлисты
- `POST /wishlists` — создать вишлист
- `GET /wishlists/:id` — получить вишлист по ID
- `PATCH /wishlists/:id` — редактировать вишлист
- `DELETE /wishlists/:id` — удалить вишлист

### 💸 Взносы (офферы)

- `POST /offers` — сделать взнос на подарок
- `GET /offers` — получить все взносы
- `GET /offers/:id` — получить взнос по ID

## 🛠️ Используемые технологии

- NestJS + TypeScript — серверное приложение
- PostgreSQL — база данных
- TypeORM — ORM
- JWT + Passport — аутентификация
- Class-validator — валидация DTO
- Swagger — авто-документация API
- bcrypt — хэширование паролей
- ESLint + Prettier — линтинг и автоформатирование

## ⚠ Особенности и безопасность

- Хэширование паролей через bcrypt
- Аутентификация через JWT (access token)
- Ограничение доступа к маршрутам через Guards
- Валидация входящих данных (DTO + pipes)
- Встроенные исключения (NotFoundException, ConflictException и т.д.)

## 🔗 Ссылка на репозиторий

https://github.com/Mercuuury/kupipodariday-backend
