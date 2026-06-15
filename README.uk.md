# Twitch Chat Downloader

> [🇬🇧 English](README.md) · [🇷🇺 Русский](README.ru.md)

Проста та швидка програма для завантаження чату з Twitch VOD. Експорт у TXT, CSV або перегляд у браузері.

![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat&logo=python)
![PyQt6](https://img.shields.io/badge/PyQt6-6.5%2B-41CD52?style=flat&logo=qt)
![License](https://img.shields.io/badge/License-MIT-3DA639?style=flat)

<p align="center">
  <img src="assets/logo.png" width="128" height="128" alt="Twitch Chat Downloader Logo">
</p>

## ✨ Можливості

- **🚀 Швидке завантаження** — багатопотоковий парсинг: одночасно скануються різні ділянки VOD
- **⚡ Висока швидкість** — до 16 потоків, значно швидше однопотокових аналогів
- **🎯 Точний таймінг** — завантаження чату за вказаний проміжок часу (Start / End)
- **🖼️ Попередній перегляд VOD** — мініатюра, назва, канал і тривалість перед завантаженням
- **📤 Три формати експорту** — TXT, CSV або перегляд у браузері з пошуком і фільтрацією
- **🌍 Багатомовність** — українська, російська, англійська (перемикання прапорцями)
- **🛑 Скасування в один клік** — кнопка Cancel у будь-який момент
- **⚙️ Налаштування потоків** — регулюйте під своє з'єднання

## 📸 Скріншоти

<p align="center">
  <img src="preview.png" width="480" alt="Головне вікно програми">
</p>

<p align="center">
  <img src="preview_chat_browser_export.png" width="480" alt="Перегляд чату в браузері">
</p>

## 📦 Встановлення

### Вимоги

- Windows 10 / 11
- Python 3.10 або вище
- pip

### Швидкий старт

```bash
git clone https://github.com/ZetHor3/twitch-chat-downloader.git
cd twitch-chat-downloader
pip install -r requirements.txt
python main.py
```

Або просто запустіть `run.bat` — скрипт сам встановить залежності та відкриє програму.

## 🎮 Використання

1. **Вставте посилання на VOD** — наприклад: `https://www.twitch.tv/videos/2796577649`
2. **Зачекайте на завантаження прев'ю** — програма покаже назву, канал і тривалість
3. **(Опціонально) Вкажіть таймінг** — Start / End для завантаження частини чату
4. **Натисніть Download Chat** — почнеться багатопотокове завантаження
5. **Експортуйте результат** — TXT, CSV або Browser (перегляд + пошук/фільтр)

## 🧵 Налаштування потоків

| Потоків | Швидкість | Навантаження на мережу |
|---------|-----------|------------------------|
| 1–2 | Низька | Мінімальне |
| 4–6 | Середня | Рекомендується |
| 8–16 | Висока | Для швидких з'єднань |

## 📁 Структура проекту

```
twitch-chat-downloader/
├── main.py                # Графічний додаток на PyQt6
├── chat_downloader.py     # Модуль завантаження чату (GQL)
├── worker.py              # Фоновий потік завантаження
├── l10n.py                # Локалізація (EN/RU/UK)
├── requirements.txt       # Залежності
├── run.bat                # Швидкий запуск на Windows
├── assets/
│   ├── logo.png           # Іконка додатка
│   └── flags/             # SVG-прапорці
├── README.md              # Англійська версія
├── README.ru.md           # Російська версія
└── README.uk.md           # Українська версія
```

## 🛠️ Технічні деталі

- **Інтерфейс**: PyQt6, кастомний рендеринг циклічного прогресу та прапорців через QPainter
- **API**: Twitch GQL (persisted query `VideoCommentsByOffsetOrCursor`)
- **Сканування**: посегментне (крок 30 секунд) — обхід блокування cursor-пагінації
- **Мережа**: httpx, багатопотоковість через `ThreadPoolExecutor`

## 📄 Формати експорту

### TXT
```
[00:00] username1: привіт!
[00:05] username2: як справи?
[00:12] username1: норм
```

### CSV
```
id,username,message,time_in_video,timestamp
abc123,username1,привіт!,0.0,2024-01-01T00:00:00Z
```

### Browser
Вбудована HTML-сторінка з пошуком по тексту, фільтром за користувачами, сортуванням.

## 📜 Ліцензія

MIT — робіть що хочете, але згадка автора вітається.

## 👤 Автор

**ZetHor3** — [GitHub](https://github.com/ZetHor3)

---

<p align="center">
  <sub>Built with Python, PyQt6 and ❤️</sub>
</p>
