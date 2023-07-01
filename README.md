
# K-Monitoring 📊

K-Monitoring є репозиторієм для тестування та експериментів з моніторингом. Використовуючи цей репозиторій, ви можете налаштувати та запустити різні механізми моніторингу для ваших додатків та систем.

## Огляд 👀

У цьому репозиторії ви знайдете стек інструментів для моніторингу:
* Prometheus 🗂️
* Open Telemetry 🌐
* Grafana 📈
* Loki 📜
* Fluent-bit 💬

## Встановлення та налаштування ⚙️

1. Склонуйте репозиторій до вашого локального середовища:

   ```bash
   git clone https://github.com/matvrus/k-monitoring.git
   cd k-monitoring
   ```

2. Найлегший спосіб запуску - використовуючи `docker-compose`.
   
   ```bash
   docker-compose up -d
   ```
   або без флагу -d щоб бачити процес
      ```bash
   docker-compose up 
   ```

3. Запустіть моніторинговий сервіс та сервіс сповіщень.

## Робота сервісів ⚙️

Кожен сервіс налаштований на окремому порті:
* Grafana: http://localhost:3002
* OpenTelemetry: http://localhost:4317
* Prometheus: http://localhost:9090

Перейдіть до сервісу Grafana та налаштуйте моніторинг до ваших потреб. Ви можете використовувати Loki для відстеження логів та Fluent-bit для обробки журналів.

🚀 Почніть експериментувати з моніторингом своїх додатків та систем за допомогою K-Monitoring!
# Проєкт: Моніторинг у Kubernetes за допомогою K-Monitoring



# Стек розгорнуто та налаштовано у dev-середовищі в Kubernetes для власного проекту. Fluentbit збирає та експортує логи проєкту та всіх нод кластеру.

## Вміст

- [K-Monitoring 📊](#k-monitoring-)
  - [Огляд 👀](#огляд-)
  - [Встановлення та налаштування ⚙️](#встановлення-та-налаштування-️)
  - [Конфігурація Fluentbit](#конфігурація-fluentbit)
  - [Доступ до моніторингових сервісів](#доступ-до-моніторингових-сервісів)
  - [Приклад використання](#приклад-використання)
  - [Допоміжні ресурси](#допоміжні-ресурси)
  - [DEMO](#demo)

## Огляд

K-Monitoring - це стек інструментів для моніторингу, який включає в себе наступні компоненти:
- Prometheus: система моніторингу та оповіщень
- Open Telemetry: набір бібліотек та агентів для збору метрик та трейсів
- Grafana: платформа візуалізації даних
- Loki: система агрегації та пошуку журналів
- Fluentbit: інструмент для збору та експорту логів

У цьому проєкті ми зосередимося на розгортанні та налаштуванні стеку моніторингу у вашому Kubernetes-середовищі, а також на налаштуванні Fluentbit для збору та експорту логів проєкту та всіх нод кластеру.

## Вимоги

Перед початком переконайтеся, що ваше dev-середовище відповідає наступним вимогам:
- Kubernetes кластер налаштовано
- Доступ до кластера та налаштування `kubectl`


Наявність `docker` та `docker-compose` для роботи зі стеком моніторингу

## Кроки розгортання

1. Клонуйте репозиторій K-Monitoring:

   ```bash
   git clone https://github.com/matvrus/k-monitoring.git
   cd k-monitoring
   ```

2. Застосуйте конфігураційні файли до вашого Kubernetes-кластера:

   ```bash
   cd yaml
   kubectl apply -f prometheus.yaml
   kubectl apply -f opentelemetry.yaml
   kubectl apply -f grafana.yaml
   kubectl apply -f loki.yaml
   ```

3. Переконайтеся, що всі компоненти успішно розгорнуті:

   ```bash
   kubectl get pods --namespace=k-monitoring
   ```

## Конфігурація Fluentbit

Fluentbit - це інструмент для збору та експорту логів. Щоб налаштувати Fluentbit для збору логів вашого проєкту та всіх нод кластеру, дотримуйтеся наступних кроків:

1. Відредагуйте файл `fluentbit-configmap.yaml` та замініть `<your_project_logs_path>` на шлях до логів вашого проєкту.

2. Застосуйте конфігураційний файл до вашого Kubernetes-кластера:

   ```bash
   kubectl apply -f fluentbit-configmap.yaml
   kubectl apply -f fluentbit-ds.yaml
   ```

3. Переконайтеся, що Fluentbit успішно розгорнуто:

   ```bash
   kubectl get pods --namespace=k-monitoring
   ```

## Доступ до моніторингових сервісів

Після розгортання стеку моніторингу, ви можете отримати доступ до наступних сервісів:

- Grafana: http://localhost:3002
- Prometheus: http://localhost:9090
- Loki: http://localhost:3100

## Приклад використання

Після успішного розгортання та налаштування стеку моніторингу, ви можете почати використовувати його для моніторингу свого проєкту. Збирання та візуалізація метрик, трейсів та логів допоможуть вам аналізувати та вдосконалювати продукт.

## Допоміжні ресурси

Додаткову інформацію та документацію можна знайти за наступними посиланнями:

- [Prometheus документація](https://prometheus.io/docs/)
- [Open Telemetry документація](https://opentelemetry.io/docs/)
- [Grafana документація](https://grafana.com/docs/)
- [Loki документація](https://grafana.com/oss/loki/)
- [Fluentbit документація](https://fluentbit.io/documentation/)


## DEMO


| Example 1 | Example 2 | Example 3 | Example 4 |
|-----------|-----------|-----------|-----------|
| ![Example 1](data/01.png) | ![Example 2](data/02.png) | ![Example 3](data/03.png) | ![Example 4](data/04.png) |

| Example 5 | Example 6 | Example 7 | Example 8 |
|-----------|-----------|-----------|-----------|
| ![Example 5](data/05.png) | ![Example 6](data/06.png) | ![Example 7](data/07.png) | ![Example 8](data/08.png) |

| Example 9 | Example 10 | Example 11 | Example 12 |
|-----------|------------|------------|------------|
| ![Example 9](data/09.png) | ![Example 10](data/10.png) | ![Example 11](data/11.png) | ![Example 12](data/12.png) |

| Example 13 | Example 14 | Example 15 | Example 16 |
|------------|------------|------------|------------|
| ![Example 13](data/13.png) | ![Example 14](data/14.png) | ![Example 15](data/15.png) | ![Example 16](data/16.png) |

| Example 17 | Example 18 |
|------------|------------|
| ![Example 17](data/17.png) | ![Example 18](data/18.png) |


Дивіться демонстраційне відео на YouTube, щоб побачити налаштований стек моніторингу в дії: ![[Example 19](https://youtu.be/Gi-2FskO0jk)](data/19.png)[Демо налаштованого стеку моніторингу](https://youtu.be/Gi-2FskO0jk).
