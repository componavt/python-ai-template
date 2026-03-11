# python-ai-template

🚀 Шаблон для курса «Основы программирования на Python с использованием ИИ»

---

# 🚀 Python + AI для начинающих программистов

Этот репозиторий — ваш **личный учебный проект** по курсу
*«Основы программирования на Python с использованием ИИ»*  
(дисциплина: *Компьютерный анализ экономических данных*)

---

## 📌 Шаг 1. Создание своего репозитория

1. Нажмите кнопку **Create a new fork** (Создать форк)
2. Назовите репозиторий:  
   `python-ai-Фамилия-Имя`  
   Пример: `python-ai-Ivanov-Ivan`

---

## 📂 Структура репозитория

После создания форка у вас будет:

```
python-ai-Ivanov-Ivan/
│
├── README.md                              # Этот файл
├── notebooks/                             # Jupyter-ноутбуки с кодом
│   ├── week2b_read_csv.ipynb             # Задание 2: чтение и анализ CSV
│   └── week3_visualization.ipynb         # Задание 3: визуализация
│
├── data/                                  # Данные и SPARQL-запросы
│   ├── entity_info.sparql                # SPARQL-запрос: основные атрибуты
│   ├── entity_info.csv                   # CSV, полученный из Викиданных
│   ├── entity_fin.sparql                 # SPARQL-запрос: финансовые данные (если нужно)
│   ├── entity_fin.csv                    # Соответствующий CSV
│   ├── entity_info_cleaned.csv           # (опционально) очищенный DataFrame
│   └── examples/                         # Примеры CSV от преподавателя
│       ├── cartoons_capital_cost.csv
│       └── cartoons_genre_country_duration.csv
│
└── prompts/                               # Таблица диалогов с ИИ
    └── README.md                          # Инструкция по заполнению
```

> **Соглашение об именах файлов:**  
> `entity` — это тема вашего датасета: `volcanoes`, `museums`, `tea_coffee` и т.п.  
> Один `.sparql`-файл → один `.csv`-файл → один тип объектов.  
> Файл `*_cleaned.csv` создаётся в задании 2 **только если** данные потребовали
> существенной обработки (парсинг координат, фильтрация, объединение файлов).
> Исходные CSV не перезаписываются.

---

## 📂 Шаг 2. Работа через Google Colab

Все ноутбуки из `notebooks/` открываются в **Google Colab**:

1. Откройте файл `.ipynb` на GitHub
2. Замените `github.com` на `colab.research.google.com/github` в URL
3. Или используйте расширение браузера «Open in Colab»

**Клонирование репозитория в Colab (начало каждого ноутбука):**

```python
import os
repo = 'python-ai-Ivanov-Ivan'  # ← замените на своё имя репозитория
if not os.path.exists(f'/content/{repo}'):
    !git clone https://github.com/ВашЛогин/{repo} /content/{repo}
%cd /content/{repo}
```

**Сохранение изменений обратно в GitHub:**
- File → Save a copy in GitHub → выберите свой репозиторий

---

## 🤖 Шаг 3. Работа с AI-платформами

Для каждого задания своя платформа:

| Задание | Платформа | Ссылка |
|---------|-----------|--------|
| 1 (SPARQL) | LeChat Mistral | https://chat.mistral.ai |
| 2 (pandas) | Qwen | https://chat.qwen.ai |
| 3 (визуализация) | DeepSeek | https://chat.deepseek.com |

**Шаблон промпта для начинающих:**

```
Ты — преподаватель Python для начинающих.
Я студент-экономист, программирую впервые.

Задача: [опишите задачу]

Требования:
- Объясняй код построчно
- Используй только базовые конструкции Python
- Если возникнет ошибка — объясни, как исправить
```

---

## 📝 Шаг 4. Фиксация работы с ИИ

**Важно!** Каждый промпт и ответ фиксируется в таблице.

### Рекомендуемый способ: Google Sheets

1. Откройте шаблон по ссылке:  
   👉 **[https://docs.google.com/spreadsheets/d/1XIahExCrwDZkISSuH2BKeGIvzp-QQy6heiYkvoUbRwc/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1XIahExCrwDZkISSuH2BKeGIvzp-QQy6heiYkvoUbRwc/edit?usp=sharing)**

2. Создайте копию: **File → Make a copy**

3. Переименуйте в: `Промпты 2026: Фамилия Имя`

4. Настройте доступ: **Share → Anyone with the link → Viewer**

**Преимущества Google Sheets:**
- ✅ Автоматическое заполнение поля `Timestamp`
- ✅ Выпадающие списки для быстрого выбора
- ✅ Не нужно коммитить изменения

---

## 🎯 Шаг 5. Выполнение заданий

Единое задание из трёх частей / Single assignment in three parts

---

### Часть 1 (Задание 1): Подготовка данных из Викиданных

**Цель:** Получить CSV-файлы с данными из Викиданных с помощью SPARQL-запросов.

**Задачи:**
1. Выберите объект для исследования в Wikidata (компании, фильмы, вулканы, памятники и т.п.)
2. Определите интересующие вас свойства объекта
3. С помощью ИИ (Mistral) напишите SPARQL-запрос и получите данные
4. Сохраните файлы в папку `data/`: запрос как `entity_info.sparql`, результат как `entity_info.csv`

**Рекомендация: несколько файлов вместо одного большого**

Если данные разнородны по структуре (например, основные атрибуты + финансовая история по годам), разделите их на два файла:

| Файл | Что содержит |
|------|-------------|
| `entity_info.sparql` / `.csv` | Координаты, страна, год основания — одна строка на объект |
| `entity_fin.sparql` / `.csv` | Выручка, сотрудники по годам — несколько строк на объект |

**Требования к данным:**
- Формат: CSV (кодировка UTF-8, разделитель — запятая)
- URI главного объекта (ссылка на Викиданные) — обязательно в SELECT и в CSV
- Источник воспроизводим: сохранён `.sparql`-файл с комментариями

**Пример диалога с ИИ:**  
👉 [Пример работы с Mistral: мультфильмы из Викиданных](https://chat.mistral.ai/chat/a9679dae-6d1a-4214-8572-a378c49c46d1)

**Примеры готовых CSV-файлов:**  
В папке `data/examples/` вы найдёте примеры CSV, полученных из Викиданных:
- `cartoons_capital_cost.csv` — мультфильмы с затратами на производство
- `cartoons_genre_country_duration.csv` — мультфильмы с жанрами, странами и продолжительностью

**Полезные ресурсы:**
- Wikidata Query Service: https://query.wikidata.org/
- Примеры SPARQL-запросов: https://www.wikidata.org/wiki/Wikidata:SPARQL_query_service/queries/examples
- Курс «Программирование Викиданных»: https://ru.wikiversity.org/?curid=23388

---

### Часть 2 (Задание 2): Анализ данных в Colab

**Цель:** Загрузить CSV из GitHub в Google Colab, изучить структуру данных и подготовить их к визуализации.

**Ноутбук:** `notebooks/week2b_read_csv.ipynb`  
**Платформа ИИ:** Qwen

**Шаги в ноутбуке:**

0. **Импорты** — все `import` только в первой ячейке
1. **Клонирование репозитория** в Colab (по абсолютному пути `/content/{repo}`)
2. **Чтение CSV** — через `pd.read_csv(...)`, вывод первых строк
3. **Очистка столбцов** — переименование, приведение типов:
   - Столбец с URI объекта **не удалять**, а переименовать в `URL`
   - Числовые столбцы: `pd.to_numeric(..., errors='coerce')`
   - OPTIONAL-поля (год смерти и аналоги) — **без** `fillna(0)`, NaN означает «данных нет»
4. **Анализ** — `.describe()`, `.value_counts()`, заполненность OPTIONAL-полей, выбросы
5. **Экспорт** *(опционально)* — если данные существенно преобразованы (распарсены координаты, отфильтрованы аномалии, объединены несколько файлов), сохранить результат:

```python
df.to_csv('data/entity_info_cleaned.csv', index=False, encoding='utf-8-sig')
```

> Если данные не требовали преобразований — шаг пропускается;  
> в задании 3 читается исходный CSV напрямую.

**Важно: «длинный формат»**  
Если CSV содержит несколько строк на один объект (из-за многозначных полей — жанры, соседи, финансовые данные по годам) — зафиксируйте это в Markdown-ячейке. Пример: «1555 строк = ~150 компаний × несколько лет финансовых данных». Это не ошибка, а особенность структуры.

---

### Часть 3 (Задание 3): Визуализация

**Цель:** Построить осмысленные графики на основе подготовленных данных.

**Ноутбук:** `notebooks/week3_visualization.ipynb`  
**Платформа ИИ:** DeepSeek

**Задачи:**
1. Прочитать данные из `data/` (исходный CSV или `*_cleaned.csv` если создан)
2. Построить не менее 3 графиков; для каждого:
   - сформулировать исследовательский вопрос
   - явно указать, по какой выборке строится график и сколько записей (N)
   - написать краткий вывод в Markdown-ячейке
3. Сохранить графики как PNG-файлы

**Инструменты:** matplotlib, seaborn (основные), plotly / folium (дополнительно)

**Обязательно для сдачи задания 3:**  
По завершении работы с DeepSeek нажмите **Share → Public link to thread**  
и включите эту ссылку в форму сдачи. Без публичной ссылки работа не может быть проверена.

---

**EN (short version):**
1. **Part 1:** Build CSV files from Wikidata using SPARQL queries; save `.sparql` and `.csv` to `data/`.
2. **Part 2:** Clone repo in Colab, read and analyze CSV with pandas (`week2b_read_csv.ipynb`).
3. **Part 3:** Visualize data with matplotlib/seaborn (`week3_visualization.ipynb`); share DeepSeek thread link.

---

## 📤 Шаг 6. Сдача работы

**Через Google Form** (ссылка будет выдана на занятии) вы отправите:

1. Ссылку на ваш репозиторий GitHub (`python-ai-Фамилия-Имя`)
2. Ссылки на диалоги с ИИ:
   - Mistral (задание 1)
   - Qwen (задание 2)
   - DeepSeek (задание 3) — **публичная ссылка Share → Public link**
3. Ссылку на вашу таблицу промптов Google Sheets (доступ «Просмотр»)

EN: Submit links to your GitHub repo, AI chat threads (Mistral, Qwen, DeepSeek public link), and your prompts table.

---

## ✅ Критерии зачёта

Зачёт ставится при выполнении **всех трёх частей** задания:

- ✅ **Часть 1:** В папке `data/` есть `.sparql`-файл(ы) и соответствующий CSV из Wikidata; URI объекта сохранён в CSV
- ✅ **Часть 2:** Ноутбук `week2b_read_csv.ipynb` запускается без ошибок (`Runtime → Run all`); столбец URL сохранён; Markdown-ячейки описывают ваши данные, а не данные шаблона
- ✅ **Часть 3:** Ноутбук `week3_visualization.ipynb` содержит не менее 3 графиков с исследовательскими вопросами и выводами; публичная ссылка на беседу с DeepSeek приложена
- ✅ **Таблица промптов:** Заполненная Google Sheets со всеми тремя заданиями

**Никакого теста нет.** Единственное условие зачёта — выполненные три части задания.

---

## 🆘 Помощь

- **Telegram-канал курса**: [t.me/PromptMagi](https://t.me/PromptMagi)
- **Вопросы преподавателю**: [@componavt](https://t.me/componavt)
- **Документация Python**: https://docs.python.org/3/
- **Google Colab FAQ**: https://research.google.com/colaboratory/faq.html
- **Wikidata Query Service**: https://query.wikidata.org/

---

## 📚 Полезные ссылки

- [Основы Python на русском](https://ru.pythontutor.ru)
- [Pandas документация](https://pandas.pydata.org/docs/)
- [Matplotlib галерея](https://matplotlib.org/stable/gallery/)
- [Wikidata SPARQL примеры](https://www.wikidata.org/wiki/Wikidata:SPARQL_query_service/queries/examples)
- [Курс «Программирование Викиданных»](https://ru.wikiversity.org/?curid=23388)

---

**Удачи! 🚀**
