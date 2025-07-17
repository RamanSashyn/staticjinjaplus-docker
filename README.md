# StaticJinjaPlus Docker Image Builder

Этот репозиторий содержит набор Dockerfile для сборки образов StaticJinjaPlus на базе различных операционных систем.

Цель порта — помочь собрать и запустить собственный образ StaticJinjaPlus с нужной версией исходников. 

Исходный код StaticJinjaPlus: https://github.com/MrDave/StaticJinjaPlus  

## Доступные Dockerfile
- `Dockerfile.ubuntu` — сборка на базе Ubuntu
- `Dockerfile.slim` — сборка на базе Python Slim

## 🔧 Как собрать свой образ

1. Клонируйте этот репозиторий или скачайте нужные Dockerfile:
```bash
git clone https://github.com/ramansashyn/staticjinjaplus-docker.git
```

2. В терминале перейдите в папку с Dockerfile:
```bash
cd staticjinjaplus-docker
```

3. Соберите нужный образ, указав версию StaticJinjaPlus и базовый образ, используя примеры ниже.

## Примеры команды для сборки

Сборка на базе Ubuntu с версией 0.1.1:
```bash
docker build -f Dockerfile.ubuntu -t yourdockerusername/staticjinjaplus:0.1.1 --build-arg STATIC_JINJA_VERSION=tags/0.1.1 .
```
Сборка последнего коммита main-ветки на базе Ubuntu:
```bash
docker build -f Dockerfile.ubuntu -t yourdockerusername/staticjinjaplus:develop --build-arg STATIC_JINJA_VERSION=heads/main .
```
Сборка на базе Python Slim с версией 0.1.1:
```bash
docker build -f Dockerfile.slim -t yourdockerusername/staticjinjaplus:0.1.1-slim --build-arg STATIC_JINJA_VERSION=tags/0.1.1 .
```
Сборка последнего коммита main-ветки на базе Python Slim:
```bash
docker build -f Dockerfile.slim -t yourdockerusername/staticjinjaplus:develop-slim --build-arg STATIC_JINJA_VERSION=heads/main .
```

## 🐳 Как запустить контейнер

```bash
docker run -it yourdockerusername/staticjinjaplus:0.1.1 bash
```

---

## 🚀 Публикация образа в Docker Hub

После сборки с полным тегом (со своим username):

```bash
docker push yourdockerusername/staticjinjaplus:0.1.1
```

---

## 💡 Важно

* Этот репозиторий **НЕ содержит исходники StaticJinjaPlus**.
* Все исходники скачиваются во время сборки напрямую из официального GitHub-репозитория [MrDave/StaticJinjaPlus](https://github.com/MrDave/StaticJinjaPlus).
* Вы можете выбрать любую доступную версию или использовать develop.
* Для разных базовых образов используйте соответствующий Dockerfile.

---

## 📃 Список доступных версий

| Тег            | База                    |
| -------------- | ----------------------- |
| `0.1.0`        | Ubuntu                  |
| `0.1.1`        | Ubuntu                  |
| `0.1.0-slim`   | Python Slim             |
| `0.1.1-slim`   | Python Slim             |
| `develop`      | Ubuntu (HEAD main)      |
| `develop-slim` | Python Slim (HEAD main) |
| `latest`       | Ubuntu (Release)        |
| `slim`         | Python Slim (Release)   |

---

## 🤝 Контакты

Автор порта: [ramansashyn](https://hub.docker.com/u/ramansashyn)

---

## 📝 Лицензия

Этот проект распространяется без включения исходников StaticJinjaPlus и служит только для сборки Docker-образов.
