# Telegram Group Users Parser

Скрипт на Python для сбора пользователей из Telegram-группы с помощью Telethon.

## Возможности

* Авторизация через Telegram API
* Получение списка групп, в которых состоит аккаунт
* Выбор нужной группы из списка
* Сбор пользователей по сообщениям группы
* Сохранение результатов в файл `users.txt`
* Вывод имени, фамилии и username пользователя

---

## Используемые библиотеки

### Telethon

Асинхронная библиотека для работы с Telegram API.

Установка:

```bash
pip install telethon
```

Проверка установки:

```bash
pip show telethon
```

---

## Получение API ID и API HASH

1. Перейдите на https://my.telegram.org
2. Войдите через свой номер телефона.
3. Откройте раздел **API Development Tools**.
4. Создайте приложение.
5. Получите:

```python
api_id = 12345678
api_hash = "xxxxxxxxxxxxxxxxxxxxxxxx"
```

---

## Настройка

Откройте файл скрипта и заполните данные:

```python
api_id = 12345678
api_hash = "xxxxxxxxxxxxxxxxxxxxxxxx"
session_name = "my_session"
```

---

## Запуск

### Linux

```bash
python3 main.py
```

### Windows

```bash
python main.py
```

---

## Первый запуск

При первом запуске Telethon запросит:

```text
Введите номер телефона:
```

После ввода номера придёт код подтверждения в Telegram.

После успешной авторизации будет создан файл:

```text
my_session.session
```

Он содержит данные авторизации.

⚠️ Не публикуйте этот файл и не загружайте его в GitHub.

---

## Как пользоваться

После запуска появится список групп:

```text
1. Group One
2. Group Two
3. Group Three
```

Введите номер нужной группы:

```text
Введите номер группы: 1
```

После этого начнётся анализ сообщений и сбор пользователей.

---

## Результат

После завершения работы будет создан файл:

```text
users.txt
```

Пример содержимого:

```text
Ivan Ivanov | @ivan
Petr Petrov | @petrov
Anna Smirnova | (ID: 123456789)
```

---

## Ограничения

* Собираются только пользователи, которые отправляли сообщения в группе.
* Пользователи без сообщений не попадут в список.
* По умолчанию анализируются последние 1000 сообщений.

Изменить лимит можно здесь:

```python
async for msg in client.iter_messages(target_group, limit=1000):
```

Например:

```python
limit=5000
```

---

## Структура проекта

```text
project/
│
├── main.py
├── my_session.session
├── users.txt
└── README.md
```

---

## Безопасность

Не публикуйте:

```text
api_id
api_hash
*.session
```

Рекомендуется добавить файл `.gitignore`:

```gitignore
*.session
users.txt
__pycache__/
```

---

## Пример вывода

```text
✅ Авторизация прошла

📋 Список чатов:

1. Test Group (ID: 123456789)
2. Work Group (ID: 987654321)

🔢 Введите номер группы: 1

📨 Собираем сообщения из: Test Group

✅ Готово! Сохранено 245 пользователей в users.txt
```

---

## Автор

Telegram Group Users Parser

Python + Telethon
