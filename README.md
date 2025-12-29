# _dop_docker_monitoring_
## Мониторинг Docker-контейнеров с помощью Grafana и Prometheus
---

## Описание проекта

В данном проекте развернут стек мониторинга Docker-контейнеров, позволяющий
отслеживать состояние и производительность контейнеров в реальном времени.

### Используемые компоненты:
- **cAdvisor** — сбор метрик контейнеров (CPU, память, сеть, диск)
- **Prometheus** — хранение и обработка метрик
- **Grafana** — визуализация метрик
- **Nginx** — тестовое веб-приложение для генерации нагрузки

```

## Архитектура

Docker containers  
↓  
cAdvisor  
↓  
Prometheus  
↓  
Grafana  

---

### Структура репозитория

```text
.
├── docker-compose.yml
├── docker-monitoring-dashboard.json
├── fixed-dashboard.json
├── grafana
│   └── provisioning
│       ├── dashboards
│       └── datasources
│           └── prometheus.yml
├── grafana-datasource.yml
├── prometheus.yml
└── webapp-dashboard.json

---

## Запуск проекта

Для запуска всех сервисов выполните команду:

```bash
docker compose up -d
```

---

### Веб-интерфейсы
- cAdvisor: http://localhost:8080
- Prometheus: http://localhost:9090
- Grafana: http://localhost:3000
- Web-приложение (nginx): http://localhost

---
## Порядок выполнения:

### Создание файлов

<img width="770" height="665" alt="image" src="https://github.com/user-attachments/assets/1f252eb0-2f3f-471d-92c0-91524b547d0c" />

<img width="742" height="282" alt="image" src="https://github.com/user-attachments/assets/6a489e16-2071-418e-92c1-e7f81e81e368" />

### Запущенные контейнеры Docker

<img width="1558" height="135" alt="image" src="https://github.com/user-attachments/assets/ee5b59a4-03b3-40dd-9e8b-153a8c427344" />

### Интерфейс cAdvisor

<img width="529" height="735" alt="image" src="https://github.com/user-attachments/assets/03337ecd-a472-49d6-8674-4436a9f8e7d6" />

### Prometheus — Targets (cAdvisor UP)

<img width="1486" height="578" alt="image" src="https://github.com/user-attachments/assets/101406b7-7951-4b89-ab7d-896f757ea70d" />

### Prometheus — метрики CPU

<img width="1889" height="606" alt="image" src="https://github.com/user-attachments/assets/5e91dfba-c896-4190-aad8-f3e5e7d76b71" />

### Grafana — без нагрузки

<img width="1917" height="997" alt="image" src="https://github.com/user-attachments/assets/ad09d37c-748a-480f-883b-3a9576600ccd" />

### Grafana — под нагрузкой

<img width="1920" height="970" alt="image" src="https://github.com/user-attachments/assets/bea6def5-69b2-4e45-a965-6058ff9a165f" />

---

## Команда генерации нагрузки (PowerShell):
```bash
# Выполнить 1000 запросов 
for i in {1..1000}; do curl http://localhost
```

---

### Анализ результатов
- При отсутствии нагрузки потребление CPU минимально
- Во время генерации HTTP-запросов наблюдается рост нагрузки
- После завершения нагрузки показатели CPU возвращаются к норме
- Grafana отображает изменения метрик в реальном времени

---

## Используемые версии
- Docker
- Docker Compose
- Prometheus
- Grafana

---

### Вывод
В ходе выполнения работы был успешно развернут стек мониторинга Docker-контейнеров
на базе cAdvisor, Prometheus и Grafana. Реализация позволяет эффективно отслеживать
нагрузку и состояние контейнеров в реальном времени.
