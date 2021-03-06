### At Telegraaf.nl, we’re always concerned with the speed of our pages. ###
- Please describe, from the moment a browser requests a page to the time a user can use it, all
the potential bottlenecks that could affect page speed.
- If you had 1 month to improve the Telegraaf.nl frontend, what would you do? Why?

#### Answers ####
- I think you need to check problems with scripts. Dirty console (with 404 errors) in browser is symptom that not everything right.
![Script's bug](http://d.snfr.us/mZkY+)
- You have so much inline scripts. I think it very difficult to maintain for all team members.
- I think you must not blend apples, armchairs on the plate of pasta. Frontend code need to divided by logical parts: templates, css, js. If you will continue write your css and js in template in future, maintainability of project will be harder and harder.
- Encapsulating your own javascript code for the clean Window object.
- Time to first byte 309ms from Russia. I don't know, may be in Amsterdam everything is ok, but 309ms - it slowly.
- Biggest part of your scripts loaded from head section. I think it's wrong. You may have some scripts in "head", but these scripts must contain data and functions without which it's impossible to load page. User forced to wait loading for all scripts on the page. He can see white page instead of content part of seconds or more.
- I think biggest part of your event handlers must have been written in js-files, use jQuery .on() method or native cross-browser equivalent if overall percent of old IE's is so big.
- I think you need cache static files.
- I think you need to use :hover pseudo-class instead inline "onmouseover" event handler for css-only customizations.

  ![Use hover instead of js everywhere if it possible](http://d.snfr.us/OaSW+)

- I think you need to perform css optimizations. It's your css code, lines about 1470-1480:
```css  
div.vidoverview .header .paging {
  color: #999;
  float: right;
  width: 494px;
  text-align: right;
  margin-right: 10px;
}

div.vidoverview .header .paging .curpage {
  color: #fff;
}
```  
  So slow. I think you know how browser read selectors. It will be do 5 actions instead  one if you use for example BEM css-naming. It will be like this:
```css  
.vidooverview__pager{
  color: #999;
  // another stuff
}

.vidooverview__pager-item_state_active {
  color: #fff;
}
```
  In this example browser needs only one action to find element on page.

- At the first month i won't to give prognosis about project. I think at the moment code on the project is different in different places. Project's team needs unified workflow. Methodology for css (like BEM, OOCSS, etc.), unified javascript style-guide. 
- After that only we can talk about project's improvements.


#### Ответы ####
- Стоит проверить доступность всех скриптов, загружаемых на странице.
![Script's bug](http://d.snfr.us/mZkY+)
- Количество inline-кода столь велико, что его наверняка трудно поддерживать.
- Не стоит смешивать яблоки и стулья на одной тарелке с макаронами. Frontend должен быть строго разделен: html, css, js. Иначе любые изменения в интерфейсе будут оборачиваться головной болью для разработчиков. Отсутствием желания работать над интерфейсом и улучшать его.
- Js-код стоит писать изолированным, чтобы не засорять глобальный объект Window, иначе возможны конфликты имен, как следствие - некорректная работа скриптов.
- Не знаю как в Голландии, а в России долгий отклик от DNS-серверов 309ms, это довольно много.
- Все скрипты грузятся в секции head страницы. Не стоит забывать, что загрузка каждого js-файла - это один запрос и его инициализация, при проблемах с которой пользователь может наблюдать белый экран. Я бы все скрипты, которые возможно перенес вниз страницы, чтобы в первую очередь загрузился документ, а уж потом весь интерактив.
- Перенос скриптов в низ страницы заставит задумать об оптимизации сценариев. Отказа от inline-обработчиков для элементов страницы.
- Стоит позаботиться о кэшировании статических файлов.
- За оформление любых элементов страницы при наведении проще использовать css и псевдо-класс :hover вместо таких конструкций.

  ![Use hover instead of js everywhere if it possible](http://d.snfr.us/OaSW+)

- Стоит выполнить css-оптимизации. Это пример вашего кода, в развернутом виде строки, примерно, 1470-1480:
```css  
div.vidoverview .header .paging {
  color: #999;
  float: right;
  width: 494px;
  text-align: right;
  margin-right: 10px;
}

div.vidoverview .header .paging .curpage {
  color: #fff;
}
```  
  Уверен, у меня нет необходимости рассказывать, как читает селекторы. Помочь браузеру можно, например, используя BEM css-нотацию, селектор вида:
```css  
.vidooverview__pager{
  color: #999;
  // another stuff
}

.vidooverview__pager-item_state_active {
  color: #fff;
}
```
  Браузер отработает быстрее. Да и в принципе, такой подход позволяет привнести большую ясность в код.

- В первый и отведенный согласно заданию месяц я бы не стал давать оценку по оптимизации проекта. В первую очередь я бы синхронизировал рабочий процесс в группе разработке интерфейсов. Налицо разношерстный код, я по большому счету я изучил только главную страницу.
- Использование единой методологии на всем проекте позволит коллегам разговаривать в одной предметной области. Добившись этого, можно уже будет приступить к реформированию проекта.
