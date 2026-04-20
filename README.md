# Test DevOps simple web app
Тестовое задание на позицию DevOps. Простое веб приложение
## Запуск проекта
```
make up
```
Или
```
docker compose up -d
```
## Проверка результата
```
curl http://localhost
```
> Ожидаемый ответ\

Hello from Effective Mobile!

## Архитектура
Client -> Nginx (port 80) -> Backend (port 8080)
- Nginx принимает HTTP-запросы
- Проксирует их на backend-сервис
- Backend отвечает простым HTTP-сервером
## Структура
.\
├── backend\
│   ├── app.py\
│   └── Dockerfile\
├── docker-compose.yml\
├── .env\
├── .env.example\
├── Makefile\
├── nginx\
│   └── nginx.conf\
└── README.md\
## Полезные команды
```
make up         # запуск
make down       # остановка
make logs       # логи
make restart    # перезапуск
make ps         # статус контейнеров
```
## Особенности реализации
- Backend работает внутри Docker-сети (не доступен снаружи)
- Используется reverse proxy через Nginx
- Настроены proxy headers:
	- Host
	- X-Real-IP 
	- X-Forwarded-For
- Используется .env для конфигурации
- Добавлен healthcheck для backend
- Makefile для удобного управления
