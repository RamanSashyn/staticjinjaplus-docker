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

## Контрольные суммы версий

| Версия      | SHA256                                                       |
|-------------|--------------------------------------------------------------|
| `0.1.0`     | `3555bcfd670e134e8360ad934cb5bad1bbe2a7dad24ba7cafa0a3bb8b23c6444` |
| `0.1.1`     | `30d9424df1eddb73912b0e2ad5375fa2c876c8e30906bec91952dfb75dcf220b` |
| `develop`   | `9adccb8fe17a40252df1a3acdea7edef4633b4ecaa8ba2dd5e0270f87ae43eab` |

❗ Указывайте нужный хеш в `--build-arg STATIC_JINJA_CHECKSUM=...` при сборке.


## Примеры команды для сборки

Сборка на базе Ubuntu с версией 0.1.1:
```bash
docker build -f Dockerfile.ubuntu -t yourdockerusername/staticjinjaplus:0.1.1 --build-arg STATIC_JINJA_VERSION=tags/0.1.1 --build-arg STATIC_JINJA_CHECKSUM=sha256:30d9424df1eddb73912b0e2ad5375fa2c876c8e30906bec91952dfb75dcf220b .
```
Сборка последнего коммита main-ветки на базе Ubuntu:
```bash
docker build -f Dockerfile.ubuntu -t yourdockerusername/staticjinjaplus:develop --build-arg STATIC_JINJA_VERSION=heads/main --build-arg STATIC_JINJA_CHECKSUM=sha256:9adccb8fe17a40252df1a3acdea7edef4633b4ecaa8ba2dd5e0270f87ae43eab .
```
Сборка на базе Python Slim с версией 0.1.1:
```bash
docker build -f Dockerfile.slim -t yourdockerusername/staticjinjaplus:0.1.1-slim --build-arg STATIC_JINJA_VERSION=tags/0.1.1 --build-arg STATIC_JINJA_CHECKSUM=sha256:30d9424df1eddb73912b0e2ad5375fa2c876c8e30906bec91952dfb75dcf220b .
```
Сборка последнего коммита main-ветки на базе Python Slim:
```bash
docker build -f Dockerfile.slim -t yourdockerusername/staticjinjaplus:develop-slim --build-arg STATIC_JINJA_VERSION=heads/main --build-arg STATIC_JINJA_CHECKSUM=sha256:9adccb8fe17a40252df1a3acdea7edef4633b4ecaa8ba2dd5e0270f87ae43eab .
```

## 🐳 Как запустить контейнер и проверить работу

1. Запуск контейнера
```bash
docker run -it yourdockerusername/staticjinjaplus:0.1.1 bash
```
2. Активировать виртуальное окружение:
```bash
source venv/bin/activate
```
3. Переименуйте папку с шаблонами(в гит репозитории папка с шаблонами называется templates_example):
```bash
mv templates_example templates
```
4. Запустите генерацию сайта по шаблону:
```bash
python3 main.py
```
5. Убедитесь, что в выводе отображается успешная генерация HTML-файлов:
```python-repl
Rendering about.html...
Rendering index.html...
...
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
