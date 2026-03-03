# Yandex Metrika Visitors

> Анализ посетителей Яндекс.Метрики по различным срезам: браузеры, устройства, ОС, география, демография

## Зачем это нужно

Этот skill анализирует аудиторию сайта по различным параметрам. Данные помогают:

- **Понять аудиторию** — какие устройства и браузеры используют посетители
- **Оптимизировать под аудиторию** — адаптировать сайт под популярные платформы
- **Географический анализ** — откуда приходят посетители
- **Демография** — возраст и пол аудитории (при наличии данных)

## Что вы получите

Отчёт в форматах CSV и Markdown с группировкой по выбранному параметру:

| Файл | Содержание |
|------|------------|
| `visitors_*.*` | Данные о посетителях с метриками: визиты, посетители, отказы, время на сайте |

## Зависимости

Требует установленный [yandex-metrika-core](https://github.com/prikotov/yandex-metrika-core)

## Установка

Skill совместим с различными AI-агентами. Примеры ниже даны для OpenCode — для других инструментов смотрите их документацию по установке skills.

```bash
# Сначала установите core
git clone https://github.com/prikotov/yandex-metrika-core.git .opencode/skills/yandex-metrika-core

# Затем этот skill
git clone https://github.com/prikotov/yandex-metrika-visitors.git .opencode/skills/yandex-metrika-visitors
```

## Использование

### Напрямую через PHP

```bash
# Топ браузеров
php .opencode/skills/yandex-metrika-visitors/visitors.php

# Распределение по устройствам
php .opencode/skills/yandex-metrika-visitors/visitors.php -b device

# Топ-10 городов
php .opencode/skills/yandex-metrika-visitors/visitors.php --by city -l 10

# Демография: возраст
php .opencode/skills/yandex-metrika-visitors/visitors.php -b age

# Демография: пол
php .opencode/skills/yandex-metrika-visitors/visitors.php -b gender
```

### Параметры группировки (`--by` / `-b`)

| Параметр | Описание |
|----------|----------|
| `browser` | Браузеры (по умолчанию) |
| `browser_version` | Браузеры с версиями |
| `device` | Тип устройства (PC, Smartphone, Tablet) |
| `os` | Операционные системы |
| `os_version` | ОС с версиями |
| `country` | Страны |
| `city` | Города |
| `age` | Возраст |
| `gender` | Пол |
| `interest` | Интересы |

### Через агента

После установки skill агент автоматически узнаёт о нём. Примеры запросов:

```
Покажи распределение посетителей по устройствам
```

```
Сделай топ-20 городов по посетителям
```

```
Проанализируй какие браузеры используют посетители сайта
```

## Результаты

Отчёты сохраняются в папку с датой:

```
metrika_reports/
└── 2026-03-03/
    ├── visitors_2026-03-03_10-30-15.csv
    └── visitors_2026-03-03_10-30-15.md
```

CSV открывается в Excel/LibreOffice, Markdown — в любом текстовом редакторе или напрямую в Obsidian.

---

> Постановка задач, архитектура, ревью — [Dmitry Prikotov](https://prikotov.pro/), реализация — GLM-5 в [OpenCode](https://opencode.ai)
