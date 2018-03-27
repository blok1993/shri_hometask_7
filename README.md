# Performance https://lifehacker.ru/:

  #### Основные проблемы
    1. Время до полной отрисовки DOM (Fully interactive) составляет от 10 до 16 секунд.
    2. Довольно большие размеры сетевых запросов: ~3000 KiB
    3. Большое количество DOM элементов на странице ~2 700
    4. Время загрузки и выполнения всех JS скриптов составляет: ~9 - 10 секунд.

  #### Что можно сделать лучше:
    1. Необходимо использовать браузерный кеш для всех ресурсов.
    2. Нужно использовать gzip сжатие для всех ресурсов. Сейчас используется не для всех. Таким образом можно будет сэкономить 80.3KiB.
    3. Внедрить использование сервис-воркеров.
    4. Необходимо использовать CDN.
    5. Стоить рассмотреть использование lazy-loading для скрытого (вне вьюпорта) контента.
    6. Имеет смысл уменьшить содержимое главной страницы, т.е. сократить кол-во DOM элементов (в 2 раза как минимум).

  ###### JS, CSS
    1. 637 KiB JavaScript кода загружается сразу, блокируя рендеринг страницы. Необходимо использовать атрибуты Async / Defer, а также перенести скрипты до 2. Нужно постараться заинлайнить некоторые стили там, где это возможно. Это также облегчит загрузку.
    3. На странице подключаются 54 Js файла и 15 css файлов. Необходимо уменьшить их количество - по возможности объединив их между собой.
    4. 20 (js / css) файлов нужно минифицировать.
    5. В некоторых css файлах есть неиспользуемые правила стилей. От них нужно избавиться, чтобы не грузить лишние KiB.

  ###### Изображения
    1. Нужно оптимизировать некоторые изображения. Таким образом уменьшиться их суммарный вес на 39 KiB.
    2. Не у всех изображений проставлен атрибут [alt] - его необходимо прописать.
    3. Форматы изображений типа JPEG 2000, JPEG XR, или WebP сжимаются лучше, чем jpeg / png, что способствует более быстрому скачиванию картинки.
    4. Подготавливать изображения заранее, соответствующие размерам блоков, в которые они помещаются.

  ###### Минорные замечания
