## О проекте

Edu.hub - портал, представляющий из себя платформу для обучения магистрантов.

![Project screenshot][product-screenshot]

### Использовано

Проект был разработан с использованием фреймворков указанных ниже.

* [![React][React.js]][React-url]
* [![Django][DjangoRest]][DjangoRest-url]



## Начало работы

Эти инструкции помогут вам настроить и запустить проект на вашей локальной машине для разработки и тестирования.

### Требования

Прежде чем начать, убедитесь, что у вас установлены следующие программные обеспечения.

* [![npm][npm]][npm-url]
* [![python][python]][python-url]
* [![Posgres][postgresql]][postgresql-url]

Также, проект можно запустить при помощи Docker. В таком случае, выше перечисленные программные обеспечения не понадобятся.

* [![Static Badge][docker]][docker-url]

### Установка

* Клонируйте репозиторий проекта.
    ```sh
    git clone --recurse https://github.com/sora-yuka/schedule.git
    ```
* Создайте файл .env в корневой директории проекта.
    ```sh
    cp .env.example .env    # Для Linux/MacOS
    copy .env.example .env    # Для Windows
    ```
    Откройте файл .env и укажите данные для подключения к вашей локальной базе данных PostgreSQL, а также другие необходимые параметры (SECRET_KEY, CORS_ALLOWED_ORIGINS, POSTGRES_...).

* Открываем консоль и пишем комманду.
    ```sh 
    docker compose up --build
    ```

_Далее, идет настройка и запуск client/server по отдельности в ручную (не рекомендуемый способ)._

#### Установка клиента

1. Установка и запуск клиента в ручную (через консоль).
   * Открываем консоль и переходим в директорию, где расположен клиент.
       ```sh 
       cd ./schedule/student-schedule__client
       ```
   * Устанавливаем зависимости.
       ```sh
       npm install 
       ```
   * Запускаем проект.
       ```sh
       npm run dev -- --host 
       ```

2. Запуск с помощью Docker (рекомендуемый способ).
   * Открываем консоль и переходим в директорию, где расположен клиент.
       ```sh 
       cd ./schedule/student-schedule__client
       ```
    * Открываем консоль и пишем комманду.
        ```sh
        docker compose up --build 
        ```

#### Установка сервера

1. Установка и запуск клиента в ручную (через консоль).
    
    _Данный способ не будет работать без redis. Для запуска на операционной системе Windows, понадобится [установить WSL2](https://learn.microsoft.com/ru-ru/windows/wsl/install) и [запустить на ней redis](https://redis.io/docs/latest/operate/oss_and_stack/install/archive/install-redis/install-redis-on-windows/)._
    * Открываем консоль и переходим в директорию, где расположен клиент.
       ```sh 
       cd ./schedule/student-schedule__server
       ```
    * Создайте файл .env в корневой директории проекта.
        ```sh
        cp .env.example .env    # Для Linux/MacOS
        copy .env.example .env    # Для Windows 
        ```
        Откройте файл .env и укажите данные для подключения к вашей локальной базе данных PostgreSQL, а также другие необходимые параметры (SECRET_KEY, CORS_ALLOWED_ORIGINS, POSTGRES_...).

    * Создайте и активируйте виртуальное окружение.
        ```sh 
        python -m venv venv    # Создание виртуального окружения
        ```
        ```sh
        source venv/bin/activate    # Активация виртуального окружения для Linux/macOS
        ```
        ```sh
        venv\Scripts\activate    # Активация виртуального окружения для Windows
        ```
    * Установите необходимые зависимости.
        ```sh
        pip install -r requirements.txt 
        ```
    * Выполните миграции базы данных.
        ```sh 
        python manage.py makemigrations
        python manage.py migrate
        ```
    * Запустите сервер.
        ```sh 
        python manage.py runserver 0.0.0.0:8000
        ```
    * Создайте супер юзера, чтобы редактировать данные на странице админа.
        ```sh 
        python manage.py createsuperuser
        ```

2. Запуск с помощью Docker (рекомендуемый способ).
    * Открываем консоль и переходим в директорию, где расположен клиент.
       ```sh 
       cd ./schedule/student-schedule__server
       ```
    * Создайте файл .env в корневой директории проекта.
        ```sh
        cp .env.example .env    # Для Linux/MacOS
        copy .env.example .env    # Для Windows 
        ```
        Откройте файл .env и укажите данные для подключения к вашей локальной базе данных PostgreSQL, а также другие необходимые параметры (SECRET_KEY, CORS_ALLOWED_ORIGINS, POSTGRES_...).

    * Открываем консоль и пишем комманду.
        ```sh 
        docker compose up --build
        ```



<!-- MARKDOWN LINKS & IMAGES -->
[product-screenshot]: ./images/image.png
[React.js]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[React-url]: https://reactjs.org/
[DjangoRest]: https://img.shields.io/badge/Django_REST-Stack?style=for-the-badge&logo=django&logoColor=%23802D2D&color=%23FFF
[DjangoRest-url]: https://www.django-rest-framework.org/
[npm]: https://img.shields.io/badge/npm-10.9.2-Stack?style=for-the-badge&logo=npm&logoColor=%23C80202&labelColor=%23000
[npm-url]: https://docs.npmjs.com/downloading-and-installing-node-js-and-npm
[python]: https://img.shields.io/badge/python-3.13.3-Stack?style=for-the-badge&logo=python&labelColor=%23000
[python-url]: https://www.python.org/downloads/
[docker]: https://img.shields.io/badge/docker-docker?style=for-the-badge&logo=docker&labelColor=%23000&color=%23000
[docker-url]: https://docs.docker.com/get-started/
[postgresql]: https://img.shields.io/badge/postgresql-16.6-database?style=for-the-badge&logo=postgresql&labelColor=%23000
[postgresql-url]: https://www.postgresql.org/download/