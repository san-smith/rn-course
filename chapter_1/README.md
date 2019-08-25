# Знакомство с платформой

В этой главе мы познакомимся с платформой React Native. Начнём с того, что научимся создавать проект и запускать его на устройстве. Затем поговорим о языке разметки `JSX`, который используется для описания интерфейса приложения. Обсудим реактивный подход, лежащий в основе фреймворка. После этого сделаем обзор возможностей для стилизации ваших компонентов и технологии Flexbox для размещения компонентов на экране.
В конце главы поговорим о том, как сделать ваши проекты более надёжными, используя статическую типизацию исходного кода.

## Подготовка к работе

Для работы с React Native  в вашей системе должны быть установлены:

- Node.js версии 8.3 или новее;
- React Native CLI — интерфейс командной строки React Native;
- Java Development Kit версии 8;
- Android Studio, если вы планируете создавать приложения для Android и Xcode — для создания приложений iOS.

### Установка Node.js

Подробности установки Node.js в вашей системе вы можете найти на сайте [https://nodejs.org/](https://nodejs.org/).

### Установка интерфейса командной строки React Native

После установки Node.js вам будет доступен `npm` (Node Package Manager) — менеджер пакетов Node.

Для установки React Native CLI выполните следующую команду в терминале:

```
$ npm install -g react-native-cli
```

### Установка Java Development Kit

React Native требуется восьмая версия Java SE Development Kit (JDK). Вы можете скачать и установить OpenJDK с сайта AdoptOpenJDK:  [https://adoptopenjdk.net/](https://adoptopenjdk.net/).

### Подготовка среды разработки Android

**Установка Android Studio**. Скачайте и установите Android Studio с официального сайта: [https://developer.android.com/studio/index.html]({https://developer.android.com/studio/index.html).

**Установка Android SDK**. Android Studio устанавливает последнюю версию Android SDK по умолчанию. Однако для создания приложения React Native с нативным кодом требуется, в частности, Android 9 (Pie) SDK. Дополнительные Android SDK можно установить с помощью SDK Manager в Android Studio.

**Настройка переменной окружения ANDROID_HOME**. Для инструментов React Native требуются некоторые переменные среды для создания приложений с нативным кодом.

Добавьте следующие строки в `$HOME/.bash_profile` или `$HOME/.bashrc` файл:
```
export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/platform-tools
```

Выполните следующую команду для загрузки настроек в текущий терминал:

```
$ source $HOME/.bash_profile
```

Также можно просто перезапустить терминал, чтобы загрузить настройки. Проверить, что `ANDROID_HOME` была добавлена в переменную окружения, можно с помощью команды:

```
$ echo $PATH
```

Теперь можно приступать к созданию первого проекта.
