# Введение

React Native - это фреймворк для разработки кроссплатформенных мобильных приложений.

Давайте начнём с небольшой справки:

- Появился в марте 2015 года.
- Как и React, куётся в недрах facebook при активном участии сообщества.
- Базируется на React.
- Используются нативные компоненты. React Native — это история не про html-страничку внутри webview. Здесь вы используете родные для системы компоненты, которыми управляете с помощью JS.
- Родной язык — JavaScript*. Со звездочкой, потому что, с одной стороны, иногда вам придется писать на Java/Objective C, а с другой — вместо JS можно использовать TS.
- Кроссплатформенный. Официально поддерживается Android и iOS, но в коммьюнити идет разработка React Native for Windows, React Native for Web и, с некоторой успешностью, реализация для десктопа. Последнее обычно построено на базе Electron.
- open source: React Native использует MIT лицензию, которую так любят разработчики. У них активное коммьюнити, часть разработки уже передали на откуп сообществу. Например, компоненты AsyncStorage и WebView выпиливают из ядра ReactNative и официально рекомендуют использовать версии этих компонентов, разрабатываемые сообществом.
- ~~77644~~ 78289 ★ на GitHub. За то время, пока я готовил вступление, звездочек стало на 645 больше.

Немного инфографики. На следующем рисунке представлена динамика популярности запросов по некоторым кроссплатформенным технологиям за последние 2,5 года. Можно увидеть, что React Native — это модный молодёжный фреймворк, которым в последнее время интересуются примерно в 2 раза чаще, чем остальными представленными технологиями.

![Динамика популярности кроссплатформенных фреймворков](./img/google-trends.png)

Из чего же состоит приложение на React Native? В первом приближении оно похоже на слоеный пирог: фактически, ваше приложение состоит из JS-мира, который с помощью Bridge APIs связан с нативным миром системы. Бизнес-логика пишется на JS, разметка пишется на JSX, а рисуется всё нативными компонентами. Bridge APIs, по понятным причинам, является узким горлышком, подробнее об этом в [документации](https://facebook.github.io/react-native/docs/performance).

![React Native rendering](https://www.altexsoft.com/media/2018/02/react-rendering.png)

### Философия React Native

Философия React Native во многом совпадает с философией своего прародителя - React:

- **Реактивное программирование**. Название говорит само за себя. На практике для нас это означает, что при изменении *стейта* или *пропсов* происходит перерисовывание сцены. Например, если вы хотите показать лоадер при загрузке данных, то нужно написать что-то вроде `this.state.inProgress && <ActivityIndicator/>`.
- **Компонентный подход**. React Native предполагает, что интерфейс вашего приложения будет состоять из компонентов, которые вкладываются в другие компоненты. Наследование компонентов не приветствуется.
- **props & state**. В  React Native, как и в React, используется концепция *пропсов* и *стейта*. Если в двух словах, пропсы — это свойства, пришедшие из родительского компонента, а стейт описывает состояние компонента.
- **Однонаправленный поток данных**. В React Native данные текут в одном направлении — от родителя к потомкам. Если хотите из дочернего компонента что-то изменить в родительском, то передавайте в дочерний компонент callback.
- **Learn once, write everywhere!** React Native не обещает, что однажды написанный код будет работать на любой платформе. Но говорит, что одинаковые подходы используются на всех платформах, так что да — однажды выучив, сможешь писать и под Android, и iOS.

### Плюсы и минусы React Native

Плюсы | Минусы
------------ | -------------
JavaScript | JavaScript
Быстрая разработка | Медленная скорость работы
Кроссплатформенность... | ...но не полная
Документация | Литературы явно недостаточно
Куча готовых пакетов | Куча готовых пакетов
Большое коммьюнити | Инструментальная поддержка
Можно использовать нативные модули | Нужно использовать нативные модули
Hot-reloading | Баги, тысячи их!
Он с нами надолго | -

Как и любой современный фреймворк, React Native не является серебрянной пулей. Есть у него свои преимущества и недостатки, которые необходимо учесть при принятии решения об использовании этого инструмента для решения вашей задачи. В таблице тезисно перечислены плюсы и минусы этой технологии (на мой взгляд), теперь давайте расшифруем эти тезисы.

Начнем с плюсов.

- В  React Native используется JS, а это достаточно простой и популярный язык с низким порогом входа. Если раньше вы занимались веб-разработкой, а тем более, если писали на  React, то вам будет легко перелезть на рельсы мобильной разработки.
- Декларативный подход к разметке интерфейса вкупе с использованием JS позволяет в кротчайшие сроки получить работающее приложение. Пока ваши коллеги на Java будут дописывать иерархию классов, вы уже будете сдавать проект заказчику.
- Жизнь слишком коротка, чтобы тратить её на разработку двух версий одного приложения. И React Native вам с этим поможет — (с некоторыми нюансами) вы сможете получить приложение сразу для двух платформ из одного проекта.
- У React Native, пожалуй, одна из лучших документаций. Там вы найдете описание компонентов и API, примеры использования — в общем, всё, что нужно разработчику.
- React Native разработчики живут в мире JS, а в этом мире есть npm, в котором куча готовых пакетов на все случаи жизни.
- У React Native огромное коммьюнити. Оно развивает React Native, создает новые компоненты и весьма дружелюбно к новичкам — вам ответят на вопросы как на StackOverFlow, так и на GitHub.
- Если какого-то функционала нет в существующих компонентах, то вы можете реализовать его с помощью нативных для платформы компонентов.
- В React Native есть такая фича как горячая перезагрузка. Как это работает: вы, например, изменяете текст в компоненте или его стили, сохраняете файл и сразу видите изменения. Нет нужды заново компилировать весь проект.
- React Native пришёл и он останется с нами надолго, как бы вы к нему не относились. Его поддерживает такой гигант как facebook, его используют крупные мировые игроки, поэтому выбрав сегодня React Native вы можете быть уверены в завтрашнем дне следующие несколько лет.

Теперь о минусах.

- В  React Native используется JS, а это весьма необычный язык со своими странностями. Особенно, если вы пришли из мира C#/Java. Приготовьтесь к тому, что первое время вы будете находиться в состоянии перманентного фейспалма и выкрикивания «WTF!». Кроме того, в крупных проектах, динамическая природа JS позволяет невозбранно выстрелить себе в ногу тысячей способов. Чтобы немного уменьшить боль разработчиков, можно использовать flow, но у него тоже есть свои тараканы. С некоторых пор можно использовать TS, что в целом выглядит обнадеживающе, но тоже есть некоторые проблемы.
- Нативные компоненты конечно же быстрее странички в WebView, но в целом React Native медленнее приложений на Xamarin и, тем более, Flutter. Особенно это становится заметно, если у вас экран с большим количеством компонентов и анимации (особенно, если эта анимация не нативна).
- Кроссплатформенность в React Native не полная. В частности, есть компоненты, специфичные для платформы. Компоненты, общие для обеих платформ, могут иметь свойства, которые работают только под одной из платформ. И, наконец, даже те свойства, которые есть в обеих платформах, могут вести себя по разному.
- Литературы явно недостаточно. Я видел 3 книги на английском и кучу статей уровня «Hello world!». Статей «для продолжающих» не то чтобы много, а на русском всё ещё печальнее.
- Куча готовых пакетов — это не всегда хорошо. Вы можете столкнуться с ситуацией, когда есть несколько пакетов, которые покрывают не пересекающуюся часть нужного вам функционала, да притом ещё и пару лет как заброшенные. Что из этого выбрать — не всегда очевидно.
- С инструментальной поддержкой пока не очень хорошо. Чего-нибудь уровня Android Studio или Visual Studio у вас не будет. Вместо этого вы возьмете VS Code, обмажетесь плагинами, сторонними утилитами и будете молиться, чтобы оно не упало. (Спойлер: не помогает).
- Иногда без использования нативных модулей просто не обойтись. В этом случае вам придется писать компонент на Java/Objective C, делать для него обертку для React Native. Если у вас приложение со специфичным функционалом, то возможно, что React Native — не ваша тема.
- Баги при разработке на React Native вам встретятся всех сортов и на любой вкус. Вы столкнетесь с багами платформ, с багами в React Native, с багами в используемых сторонних компонентах и, наконец, с багами в вашем коде. Поэтому приготовьтесь к забегу по StackOverFlow и GitHub. Что, впрочем, не всегда помогает, потому что новые версии появляются как горячие пирожки, да так, что предыдущие рецепты не работают.

Несмотря на указанные недостатки, React Native является весьма достойным инструментом для разработки мобильных приложений. Кроме того, многие из этих недостатков связаны с молодостью проекта (на момент написания этих строк, стабильная версия — 0.60) и с течением времени будут устранены.

Если вы ещё не передумали изучать особенности разработки мобильных приложений в React Native, то переходите к главе [Знакомство с платформой](./chapter_1/README.md).