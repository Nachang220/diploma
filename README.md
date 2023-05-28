# Приложение клининговой компании ССLean

Этот проект представляет собой web-приложение для компании предоставляющей услуги клинига.

## Инструменты

- Python >= 3.11.3
- Django Framework

## Установка

1. Скачайте репозиторий приложения на свой локальный компьютер. Вы можете сделать это, выполнив следующую команду:

   ```bash
   git clone https://github.com/Nachang220/diploma.git
   ```

2. Перейдите в каталог проекта:

   ```bash
   cd cclean
   ```

3. Создайте виртуальное окружение для приложения:

   ```bash
   python -m venv venv
   ```

4. Активируйте виртуальное окружение:

   ```bash
   venv\Scripts\activate
   ```

5. Установите необходимые зависимости, выполнив команду:

   ```bash
   pip install -r requirements.txt
   ```

6. Создайте базу данных и файлы миграции для приложения:

   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

7. Загрузите начальные данные в базу данных, используя фикстуры:

   ```bash
   python manage.py loaddata cleaning.json
   ```

8. Запустите локальный сервер разработки:

   ```bash
   python manage.py runserver
   ```

9. Перейдите по адресу [http://localhost:8000](http://localhost:8000) в вашем веб-браузере, чтобы открыть приложение.

## Yookassa

1. В первую очередь, вам нужно зарегистрироваться
   на [Yookassa](https://yookassa.ru/yooid/signup/step/phone?origin=Checkout&returnUrl=https%3A%2F%2Fyookassa.ru%2Fjoinups%3FcreateTestShop%3Dtrue)
   и создать тестовый магазин. Здесь вы также можете найти свой **идентификатор магазина**.

   ![alt text](https://i.ibb.co/HT4czhY/2023-05-28-163540044.png)

2. Следующим шагом вам нужно получить **API-ключ**.

   ![alt text](https://i.ibb.co/nk3V39Q/2023-05-28-161735527.png)

3. Измените файл .env в корне приложения:
   ```dotenv
   YOOKASSA_SHOP_ID=ваш идентификатор магазина
   YOOKASSA_SECRET_KEY=ваш секретный ключ
   ```

4. Если вы запускаете проект локально, установите дополнительно **ngrok**:
    - Перейдите на официальный сайт [ngrok](https://ngrok.com) и зарегистрируйтесь;
    - Скачайте утилиту;
    - Распакуйте содержимое архива в удобное место на вашем компьютере;
    - Найдите ваш токен авторизации и сохраните его:
      ![alt text](https://i.ibb.co/9rP9PBK/2023-05-28-170251121.png)
    - Запустите исполняемый файл **ngrok.exe**;
    - В открывшемся терминале исполните команду:
      ```shell
      ngrok config add-authtoken ваш_токен_авторизации
      ```
    - Исполните следующую команду, чтобы пробросить локальный порт в интернет:
      ```shell
      ngrok http 8000
      ```
    - Скопируйте внешний адрес:
      ![alt text](https://i.ibb.co/yqDF9YV/terminal.png)

5. Добавьте внешний адрес в настройки Yookassa:

   ![alt text](https://i.ibb.co/TKSfDDN/2023-05-28-173010099.png)

   А так же в файл .env в корне проекта:
   ```dotenv
   DJANGO_ALLOWED_HOSTS=658d-78-37-19-65.ngrok-free.app
   DJANGO_CSRF_TRUSTED_ORIGINS=https://658d-78-37-19-65.ngrok-free.app
   ```
6. Теперь приложение запущено и работает в интернете по вашему
   адресу [https://658d-78-37-19-65.ngrok-free.app](https://658d-78-37-19-65.ngrok-free.app)

## Использование

После установки и запуска приложения, вы можете выполнять следующие действия:

- Регистрация нового аккаунта;
- Вход в существующий аккаунт;
- Сброс пароля;
- Просмотр доступных услуг и их подробную информацию;
- Заказ услуги на выполнение;
- Просмотр предстоящих/завершённых услуг.
