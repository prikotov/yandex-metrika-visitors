---
name: yandex-metrika-visitors
description: Анализ посетителей из Яндекс.Метрики по различным срезам
---

## Когда использовать

- Анализ аудитории сайта
- Определение популярных браузеров и устройств
- География посетителей
- Демографический анализ

## Запуск

```bash
php .opencode/skills/yandex-metrika-visitors/visitors.php [опции] [дата_от] [дата_до]
```

### Параметры дат

- `дата_от` — начало периода (формат: YYYY-MM-DD), по умолчанию 30 дней назад
- `дата_до` — конец периода (формат: YYYY-MM-DD), по умолчанию сегодня

### Опции

| Опция | Сокращение | Описание | Значения | По умолчанию |
|-------|------------|----------|----------|--------------|
| `--by` | `-b` | Группировка | `browser`, `browser_version`, `device`, `os`, `os_version`, `country`, `city`, `age`, `gender`, `interest` | `browser` |
| `--sort` | `-s` | Поле сортировки | `visits`, `visitors`, `bounce_rate`, `page_depth`, `avg_duration` | `visits` |
| `--order` | `-o` | Направление сортировки | `asc`, `desc` | `desc` |
| `--limit` | `-l` | Лимит записей | число (например: 10, 20, 50) | все записи |

### Примеры

```bash
# Топ браузеров за 30 дней
php .opencode/skills/yandex-metrika-visitors/visitors.php

# Топ-10 браузеров с версиями
php .opencode/skills/yandex-metrika-visitors/visitors.php -b browser_version -l 10

# Топ-20 городов по посетителям
php .opencode/skills/yandex-metrika-visitors/visitors.php --by city --sort visitors -l 20

# Распределение по устройствам
php .opencode/skills/yandex-metrika-visitors/visitors.php -b device

# Операционные системы с версиями
php .opencode/skills/yandex-metrika-visitors/visitors.php -b os_version

# Демография: возраст
php .opencode/skills/yandex-metrika-visitors/visitors.php --by age

# Демография: пол
php .opencode/skills/yandex-metrika-visitors/visitors.php --by gender

# Страны с наибольшим процентом отказов
php .opencode/skills/yandex-metrika-visitors/visitors.php -b country -s bounce_rate -l 10

# За определённый период
php .opencode/skills/yandex-metrika-visitors/visitors.php -b city -l 15 2025-01-01 2025-01-31
```

## Результат

`metrika_reports/YYYY-MM-DD/`:
- `visitors_YYYY-MM-DD_HH-MM-SS.csv` / `.md` — данные о посетителях

### Поля в отчете

| Поле | Описание |
|------|----------|
| `value` | Значение группировки (браузер, город и т.д.) |
| `visits` | Визиты |
| `visitors` | Посетители |
| `pageviews` | Просмотры страниц |
| `bounce_rate` | Процент отказов |
| `page_depth` | Глубина просмотра |
| `avg_duration` | Среднее время на сайте (сек) |
