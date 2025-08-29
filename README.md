# 🕷️ Web Scraper for divan.ru — Lighting Products Parser

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Scrapy](https://img.shields.io/badge/Scrapy-2.12-orange)
![License](https://img.shields.io/badge/License-MIT-green)

Проект представляет собой **веб-скрапер на Python с использованием Scrapy**, разработанный для автоматического сбора данных о **светильниках** с сайта [divan.ru](https://www.divan.ru).  
Парсер извлекает название, цену и ссылку на каждый товар в категории *«Освещение»* и сохраняет данные в удобном формате.

---

## 📌 Функционал
- Парсинг товаров по категории **«Освещение»** (URL: `https://www.divan.ru/search?ProductSearch%5Bname%5D=освещение&no_cache=1`)
- Извлечение:
  - Название светильника (`div.lsooF span::text`)
  - Цена (`div.py3d2 span::text`)
  - Прямая ссылка (`a[href]`)
- Поддержка пагинации (автоматическое перелистывание страниц)
- Логирование процесса через `self.logger.info()`
- Сохранение данных в JSON, CSV или других форматах

---

## 🛠️ Технологии
- `Python 3.12` (на момент разработки)
- `Scrapy 2.12.0` — основной фреймворк для веб-скрапинга
- `CSS-селекторы` — для точного извлечения данных
- `logging` — для отслеживания прогресса и ошибок
- `requests`, `Twisted`, `w3lib` — вспомогательные библиотеки

---

## 🚀 Установка и запуск

1. Клонируй репозиторий:
   ```bash
   git clone https://github.com/ваш-ник/divan-scraper.git
   cd divan-scraper
   ```

2. Создай виртуальное окружение и установи зависимости:
   ```bash
   python -m venv venv
   venv\Scripts\activate  # Windows
   # или source venv/bin/activate  # macOS/Linux
   pip install -r requirements.txt
   ```

3. Запусти spider:
   ```bash
   scrapy crawl divannewpars -o lighting_data.json
   ```

   Результат будет сохранён в файл `lighting_data.json`.  
   Поддерживаются форматы: `.json`, `.csv`, `.xml`, `.jl`.

---

## 📁 Структура проекта
```
divan_parser/
├── scrapy.cfg
├── divan_parser/
│   ├── __init__.py
│   ├── items.py
│   ├── pipelines.py
│   ├── settings.py
│   └── spiders/
│       └── divannewpars.py  ← Основной spider
└── requirements.txt
```

> 🔍 Главный файл: `spiders/divannewpars.py`  
> В нём реализован класс `DivannewparsSpider`, который использует CSS-селекторы и логирование для сбора данных.

---

## 📝 Лицензия
Этот проект распространяется под лицензией **MIT**. Подробнее — в файле `LICENSE`.

---

💡 **Хочешь улучшить проект?**  
Приветствуются предложения по улучшению (pull requests), исправлению багов и добавлению новых функций!
