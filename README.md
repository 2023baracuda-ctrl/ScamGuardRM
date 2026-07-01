# ScamGuard — официальный сайт

Лендинг и юридические документы приложения ScamGuard.  
Хостинг: Cloudflare Pages.

## Структура

```
index.html              ← лендинг, языки переключаются JS (RU/RO/EN)
privacy-{ru|ro|en}.html ← Политика конфиденциальности
eula-{ru|ro|en}.html    ← Пользовательское соглашение
css/style.css           ← все стили
img/                    ← изображения (иконка, скриншоты, favicon)
```

## Как задеплоить (один раз)

### Шаг 1 — Создать репозиторий на GitHub

1. На github.com → **New repository**
2. Имя: `scamguard-site` (или любое другое)
3. Видимость: **Public** (для бесплатного Cloudflare Pages)
4. Не добавляй README, .gitignore — мы их сами создадим
5. **Create repository**

### Шаг 2 — Залить файлы

Самый простой способ на телефоне:

1. На главной странице нового пустого репо → **uploading an existing file**
2. **Drag and drop** распакованную папку (или выбери все файлы и папки)
3. Внизу — commit message «Initial site» → **Commit changes**

Альтернативно через github.dev (нажми `.` на пустом репо) → перетащи папку слева → Source Control → Commit & Push.

### Шаг 3 — Подключить Cloudflare Pages

1. Cloudflare Dashboard → **Workers & Pages** → **Create application** → **Pages** → **Connect to Git**
2. Авторизоваться через GitHub → выбрать репозиторий `scamguard-site`
3. Настройки сборки:
   - **Production branch:** `main`
   - **Build command:** (пусто — у нас статика)
   - **Build output directory:** `/` (корень)
4. **Save and Deploy**

Через 1-2 минуты сайт будет доступен по адресу `scamguard.pages.dev`.  
Если имя занято — Cloudflare предложит другое (например `scamguard-123.pages.dev`).

### Шаг 4 — (опционально) подключить свой домен

Когда купишь `scamguard.md` или другой домен:

1. В Cloudflare Pages → проект → **Custom domains** → **Set up a custom domain**
2. Введи `scamguard.md`
3. Cloudflare сам настроит DNS-записи если домен у них же
4. Если домен у другого регистратора — добавь CNAME-запись на `scamguard.pages.dev`

## Обновления

После деплоя любое изменение в репозитории автоматически перевыкатится:

1. Отредактируй файл на github.com или через github.dev
2. Commit → Push
3. Cloudflare Pages автоматически пересоберёт и опубликует за ~30 секунд

## Что нужно править в первую очередь

В файлах после деплоя:

- **Ссылка на APK** — сейчас `https://github.com/2023baracuda-ctrl/ScamGuard/releases`. Если репо приложения переименуют — поправь в `index.html`.
- **Email** — `scamguardrm@gmail.com` указан в нескольких местах
- **Telegram** — пока пусто. Когда создашь канал, добавишь блок в footer и/или контакты.
- **Скриншоты** — `img/screenshot-home.jpg` и `img/screenshot-alert.jpg`. Если интерфейс приложения изменится — обнови.

## Локальный просмотр

Просто открой `index.html` в браузере — всё работает без сервера. Никаких зависимостей.

Если нужна разработка с автоперезагрузкой — любой простой статический сервер сгодится:

```bash
python3 -m http.server 8000   # потом открыть http://localhost:8000
```

## Лицензия

Тексты документов (Privacy / EULA) — личная собственность разработчика, переиспользование требует разрешения.  
Стилевая часть (CSS / структура HTML) — свободно для использования в личных проектах.
