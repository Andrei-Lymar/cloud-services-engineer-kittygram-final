# 🐈 Kittygram — Социальная сеть для котиков
### Полноценное Django + React приложение для обмена фотографиями котиков.

## 📁 Структура

```
kittygram-final
├── backend/                   # Django app
├── frontend/                  # React app
├── nginx/                     # Nginx config
├── infra/                     # Terraform configuration
├── .github/workflows/         # CI/CD workflows
└── docker-compose.production.yml
```

## Настройка и запуск

1. Запуск контейнеров:

```bash
docker compose -f docker-compose.production.yml up --build
```

2. Сбор статики и миграции:

```bash
docker compose exec backend python manage.py collectstatic --noinput
docker compose exec backend python manage.py migrate
```

## Деплой в Я.Облако

1.

```bash
cd infra/
terraform init
```

2.

```bash
terraform apply -auto-approve
```

После развертывания тераформом используйте IP VM.


## Необходимые переменные

| Переменная | Описание |
|--------|-------------|
| `DOCKER_USERNAME`, `DOCKER_PASSWORD` | Учетные данные докера |
| `SSH_PRIVATE_KEY`, `SERVER_HOST`, `SERVER_USER` | Данные для доступа к серверу |
| `POSTGRES_USER`, `POSTGRES_PASSWORD`, `POSTGRES_DB`, `POSTGRES_HOST`, `POSTGRES_PORT` | Настройки БД |
| `YC_CLOUD_ID`, `YC_FOLDER_ID`, `YC_KEY_JSON`, `SSH_KEY` | Настройки Я.Облака |
| `ACCESS_KEY`, `SECRET_KEY` | Настройки бакета |
| `TELEGRAM_TOKEN`, `TELEGRAM_TO` | Настройки Телеграм |

## Доступно

- Приложение: `http://<EXTERNAL_IP>/`
- Админка: `http://<EXTERNAL_IP>/admin/`
