### At Telegraaf.nl, we’re always concerned with the speed of our pages. ###
- Please describe, from the moment a browser requests a page to the time a user can use it, all
the potential bottlenecks that could affect page speed.
- If you had 1 month to improve the Telegraaf.nl frontend, what would you do? Why?

#### Ответы ####
1. Стоит проверить доступность всех скриптов, загружаемых на странице.
2. Количество inline-кода столь велико, что его наверняка трудно поддерживать.
3. Не стоит смешивать яблоки и стулья на одной тарелке с макаронами. Frontend должен быть строго разделен: html, css, js. Иначе любые изменения в интерфейсе будут оборачиваться головной болью для разработчиков. Отсутствием желания работать над интерфейсом и улучшать его.
4. Js-код все-таки стоит писать изолированным, чтобы не засорять глобальный объект Window, иначе возможны конфликты имен, как следствие - некорректная работа скриптов.
5. Не знаю как в Голландии, а в России долгий отклик от DNS-серверов 309ms, это довольно много.
6. Все скрипты грузятся в секции head страницы. Не стоит забывать, что загрузка каждого js-файла - это один запрос и его инициализация, при проблемах с которой пользователь может наблюдать белый экран. Я бы все скрипты, которые возможно перенес вниз страницы, чтобы в первую очередь загрузился документ, а уж потом весь интерактив.
7. Перенос скриптов в низ страницы заставит задумать об оптимизации сценариев. Отказа от inline-обработчиков для элементов страницы.
8. Стоит позаботиться о кэшировании статических файлов.