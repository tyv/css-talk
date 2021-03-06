

Кому интересно про меня уже прочитали на сайте wsd, не тратим время, поехали

---

Давайте признаемся, — мы подсели на транспайлеры.
Крепко сидим на сахаре. 
— Здравствуйте, меня зовут, Юра и я использую Stylus.

И в JavaScript, и в CSS никто не пишет на Vanilla.

---

Давайте поговорим об этом. 
Про препроцессоры. 
Я хоть и олдфаг, но не считаю их 100% злом.

Мое мнение простое, если ты осознаешь зачем используешь препроцессор и понимаешь какой будет результат и как его поддерживать — то это очевидное добро.

---

'CSS is a compile target' они говорят.
И хотя это было сказано в докладе про css modules, но это справедливо и для мира препропроцессоров 

Мироздание вовремя подкидывает примеры. Как только я понял, что хочу сделать этот доклад, кто-то раскопал релиз сайта авиакомпании Ryanair и среди сообщества пробежали ссылки на их 3+ mb css.

--- 

Вот пример одного правила из их файла.

Так бывает, если вы не осознаете как использовать extend.

---

* extend провоцирует дублирование селекторов 

--- 

* variables склонны иметь коллизии имен, особенно при использовании библиотек

Смотря на этот файл вы не имеете ни малейшего представления какой окажется переменная.

--- 

* mixin провоцирует дублирование свойств

В какой-то момент вы можете легко потерять контроль над результатом. 

--- 

* ```nesting``` провоцирует делать селекторы слишком специфичными.

Становится тяжело поддерживать код, когда вы хотите модифицировать какой-то элемент в зависимости от контекста.

---

* для дебага нужна дополнительня инфраструктура с поддержкой source maps

--- 

* препроцессоры провоцируют программировать на css

С Антоном Немцевым, чей доклад будет чуть позже, я судил работы верстальщиков в UA web challenge — собственно как раз сегодня финал и пока все будут на афтепати мне прийдется еще попотеть и проверить финалистов.

И там я увидел весьма сложные вычисления, которые были абсолютно ни к чему, просто _because we can_ 

--- 

Давайте посмотрим пример, по условиям конкурса я не знаю автора этой работы, поэтому я с чистой совестью рассматриваю этот пример, как пример в вакууме

* ```programming/index.scss```

---

В реальной жизни такой код совершенно бесполезен и поддерживать его совершенно невозможно.
Не программируйте на CSS. 
Хотел бы сказать, что если и начинаете это делать, то делайте это хорошо.
Но нет, просто не программируйте на CSS

---

Так как больше не существует такой профессии как верстальщик, CSS сегодня используют в работе или дизайнеры, или фронтенд разработчики или будущие дизайнеры и фронтенд разработчкик, которых мы по инерции еще называем верстальщиками... 
И как раньше начинали с узучения jQuery вместо JavaScript'а, сегодня начинают изучать препроцессоры, а не CSS и в результате мы "маемо те, що маемо".

---

И **сейчас важный момент** — так как с одной стороны у нас профессионалы, которые пишут _в том числе_ CSS, а с другой новички...

---

...CSS плохо знают намного больше людей, чем во времена до расцвета CSS3. Когда такая профессия действительно имела смысл.

Нет это не противоречие, а скорее проблема — знать нужно сегодня очень много и CSS в том числе, но он почему-то уровень знаний CSS очень заметно пострадал в этой войне. 

И мне кажется очень незаслуженно.

---

И, чтобы ситуацию немного исправить, CSS нужно популяризировать, не как compile target, а как инструмент.

Поэтому я попробую это сделать на отдельно взятой конференции :)

Расскажу о том, что будет **the next big thing** в мире CSS.

---

### Мы поговорим о

* Shapes и Masking
* я расскажу что нового случится в мире background
* покажу как работают CSS Variables
* мы взглянем на grid layout
* и помолчим о новоых селекторах

---

### CSS Shapes, CSS Masking

---

* лучше инлайн картинки, чтобы не моргало
* картинки для shapes должны быть CORS friendly, так что забудьте про разработку без сервера
* для shapes можно обойтись без картинок

---

#### initial-letter-wrap

из схожего обсуждается возможность свойства ```initial-letter-wrap``` для ```::first-letter```, что в таком листинге 

```
p::first-letter {
  initial-letter: 3;
  initial-letter-wrap: all;
}
```

может дать такую картинку
http://www.w3.org/TR/2015/WD-css-inline-3-20150917/images/A-wraparound.png

---

###CSS Image Values and Replaced Content Module Level 4

* ```element(#someId)``` позволит рендерить DOM-узел как изображение. Например параграф в качестве фона или отрендерить слайд презентации в превью
* ```conic-gradient()``` — очень ждем! Сможем рисовать красивые хромированные контролы и прекрасные pie charts!

вкупе с blending modes, который я опущу в этом докладе, — это уже совсем фотошоп.

---

###CSS Custom Properties for Cascading Variables Module Level 1 (Working draft)

---

* совсем скоро!
* харянтся в селекторах => есть специфичность и наследование
* не очень понятно как теперь будут транспайлиться переменные из препройессоров

---

###CSS Grid Layout Module Level 1

* пожалуй, самая ожидаемая спецификация
* очень большая и сложная, много новых значений и свойств, это не просто замена таблицам или флексбоксам — это целый ИНСТРУМЕНТИЩЕ для построения лэйаутов.
* весь лэйаут строится исключительно в CSS, не требуется никакой дополнительной разметки
* давайте рассмотрим простой пример 
  *  ```/examples/grid/01.html```
  *  ```/examples/grid/02.html```
* это очень упрощенная демонстрация возможностей, пожалуй это самый the next big thing из всего что я перечислил 

---

###Selectors Level 4

---

Ну что, я очень надеюсь, что немного помог вернуть интерес фронтенд разработчиков к CSS как к инструменту, а не просто compile target и средству раскрасить кнопки.

Профессиональный фроентенд разработчик должен знать на одинаково высоком уровне и CSS и JavaScript. 

Так же как и целую кучу сопутсвующих знаний: 

* как настроить сборку
* как работает браузер
* как настроить вебсервер
* какие способы кеширования данных есть
* оптимизация ресурсов
* и еще много всего

Стремитесь такими быть.

---

