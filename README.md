# Парсер книг

Парсер скачивает книги из раздела ["Фантастика"](http://tululu.org/l55/) с сайта бесплатной библиотеки http://tululu.org/

## Установка

Python 3.7 должен быть уже установлен. 
Затем используйте `pip` для установки зависимостей:
```
pip install -r requirements.txt
```

## Использование

Переходим в каталог с программой.
Команда -

```
python main.py
```

Можно также запускать с аргументами, кроме текста сообщения аргументы имеют параметры по умолчанию.

```
usage: main.py [-h] [--start_page START_PAGE] [--end_page END_PAGE] [--filename FILENAME] [--skip_txt=False] [--skip_images=False] [--dest_folder DEST_FOLDER]

optional arguments:
  -h, --help            show this help message and exit
  --start_page START_PAGE
                        Номер страницы, с которой начать скачивание (по умолчанию 1)
  --end_page END_PAGE
                        Номер страницы, на которой закончить скачивание
  --filename FILENAME
                        Имя json-файла, в который сохраняются данные  
  --skip_txt
                        Пропустить загрузку файлов книг (по умолчанию False)
  --skip_images
                        Пропустить загрузку изображений книг (по умолчанию False)
  --dest_folder DEST_FOLDER
                        Директория для хранения файлов. В данной директории создается json-файл с данными, а также папки books и images для хранения текстов и обложек книг (по умолчанию директория в которой находится скрипт)
```

## Примеры использования

```
python main.py --start_page=1 --end_page=10 --filename=book.json --skip_images=True  --dest_folder=library
```
Парсер скачает книги с 1 по 10 страницу. Изображения не будут загружены. Выходной файл с данными - **book.json** в директории **library**. Директория с текстами книг - **library/books/**. 

```
python main.py --start_page=20 --end_page=30 --filename=book.json --skip_txt=True
```
Парсер скачает книги с 20 по 30 страницу. Тексты книг не будут загружены. Выходной файл с данными - **book.json** в директории, где находжится скрипт. Изображения будут в папке **images**, в директории со скриптом.

## Пример JSON файла

```
[
  {
    "title": "Алиби",
    "author": "ИВАНОВ Сергей",
    "img_src": "images\\239.jpg",
    "book_path": "books\\Алиби.txt",
    "comments": [
      "Детский вариант анекдотов про Шерлока Холмса)",
      "Загадки я люблю.)))",
      "А мне понравилось, люблю, знаете ли, всякие загадочки, головоломочки, кроссвордики, Гимнастика ума, одним словом... \nВо всём можно найти положительные моменты, не разгадал загадку, так хоть гренки научился готовить отменные... :-)",
      "Очень поучительное для ребенка 10 лет."
    ],
    "genres": [
      "Научная фантастика",
      "Прочие Детективы"
    ]
  }
]
```