# English Ladder PWA: что делать дальше

## Что уже добавлено

- Главная страница: `english-study-coach.html`
- PWA manifest: `manifest.webmanifest`
- Service worker: `sw.js`
- Офлайн-страница: `offline.html`
- Иконки: `pwa-assets/`

## Что где менять

### 1. Внешний вид приложения

- Основной интерфейс: `english-study-coach.html`
- Цвет темы для iPhone/браузера:
  - `meta name="theme-color"` в `english-study-coach.html`
  - `theme_color` и `background_color` в `manifest.webmanifest`

### 2. Название и иконка

- Название на домашнем экране:
  - `title` в `english-study-coach.html`
  - `name` и `short_name` в `manifest.webmanifest`
- Иконка:
  - исходник: `pwa-assets/icon.svg`
  - PNG для установки: `pwa-assets/icon-192.png`, `pwa-assets/icon-512.png`, `pwa-assets/apple-touch-icon.png`

### 3. Что будет доступно офлайн

- Кэшируемые файлы: `sw.js`, массив `APP_SHELL`
- Если добавишь новые локальные файлы, впиши их туда
- После изменения `sw.js` лучше менять и `CACHE_NAME`, чтобы обновление точно подтянулось

### 4. Логика учебы

- Недельные фокусы: массив `weeks` в `english-study-coach.html`
- 7-дневный микроцикл: массив `cycleDays` в `english-study-coach.html`
- Локальное хранение: ключ `STORAGE_KEY` в `english-study-coach.html`

### 5. База данных

- Схема под Supabase: `supabase/migrations/002_english_learning_schema.sql`
- Когда подключим backend, фронт будет писать туда вместо `localStorage`

## Как запустить локально на Mac

### Вариант 1. Просто проверить в браузере

Открой `english-study-coach.html` в браузере. Интерфейс и локальное сохранение будут работать.

### Вариант 2. Проверить именно PWA-режим

Нужен локальный сервер.

Пример:

```bash
cd "/Users/antonerosenko/Documents/New project"
python3 -m http.server 8000
```

Потом открой:

```text
http://localhost:8000/english-study-coach.html
```

На Mac service worker будет работать на `localhost`.

## Как поставить на iPhone

Для iPhone нужен HTTPS-адрес. Самый простой путь:

1. Залить эти файлы на любой статический HTTPS-хостинг.
2. Открыть ссылку в `Safari` на iPhone.
3. Нажать `Поделиться`.
4. Выбрать `На экран Домой`.
5. Запустить с иконки.

## Самый практичный маршрут дальше

1. Подправить текст и недельные фокусы под твой стиль в `english-study-coach.html`.
2. Проверить страницу локально на Mac.
3. Выложить статические файлы на HTTPS.
4. Установить на iPhone.
5. Только после этого подключать Supabase и авторизацию.

## Что я бы делал следующим шагом

1. Подключил Supabase к этой странице.
2. Сделал экран `История` с календарем и недельными графиками.
3. Добавил быстрые кнопки `Открыть British Council`, `Открыть VOA`, `Открыть Anki`.
4. Добавил экспорт/импорт и синхронизацию между Mac и iPhone.
