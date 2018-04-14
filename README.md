# Тралива
> Фрэймворк для разработки веб-сайта и нативных десктопного и мобильного приложений единым проектом

## Создание проекта

Для работы вам потребуется наличие в системе специального [компилятора](https://github.com/1024sparrow/compiler).
Если вы являетесь пользователем Ubuntu (или Debian, или Mint), то установить его можно, выполнив скрипт install_compiler_ubuntu.sh (в данной репозитории) в какой-нибудь директории типа ~/opt/ .

Запустите скрипт init.sh из той директории, в которой будет располагаться проект.

Последовательность действий для создания проекта:

    1. Создайте директорию под ваш проект. Зайдите в неё.
    2. Скачайте данный репозиторий со скриптами следующей командой:
```sh
$ git clone https://github.com/1024sparrow/traliva_starter.git
```
      (возможно, сейчас вам необходимо поставить в систему компилятор)
      Заходить в появившуюся директорию не нужно.
    3. Запустите скрипт инициализации
```sh
$ traliva_starter/init.sh
```

## Порядок разработки проекта

Ознакомьтесь со [спецификацией](https://traliva.ru/spec/v1/index.html) фреймворка Тралива. Локальную копию документа найдёте в директории traliva_doc, созданной скриптом init.sh.

Этапы разработки следующие:

1. Составление спецификации.
    Составьте html-документ, в котором опишите, какое приложение вы пишете. Четыре раздела: объект состояния, компоненты, композиция, низкоуровневый API.

    1.1 Композиция.
        Нарисуйте в графическом редакторе экранные формы - как оно должно выглядеть. Опишите, что должно происходить при нажатии на каждую кнопку, приложите экранные формы необходимых диалоговых окон, экранные формы окна приложения в разных режимах работы.

    1.2 Компоненты.
        Опишите, какие компоненты (виджеты) вам потебуются. Опишите, какие данные этим компонентым должны задаваться через объект состояния, а какие - через "опции"(задаются один раз при создании компонента, задают такие параметры, как редактируемость, цвет, наличие рамочки и т.п., т.е. те параметры, которые не будут меняться во время жизни компонента).

    1.3 Объект состояния.
        Опишите структуру объекта состояния, которая бы полностью описывала состояние вашего приложения. Для свойств объекта состояния опишите также, для каких компонентов они предназначены: кто эти свойства будет менять, кто будет реагировать на изменения этих свойств, приложите ссылки на соответствующие компоненты. Возможно, вы захоите добавить в Компоненты какие-то чисто логические обработчики.

    1.4 Низкоуровневый API.
        Если предполагается сборка под платформу PC или Мобильное приложение, то, возможно, такие вещи как работа со звуком, сохранением пользовательских данных, вам понадобится пропустить через API. Опишите, какие в API должны быть функции, а также что они должны делать на каждой платформе - сайт, мобильное приложение, PC-приложение.

    Написание спецификации избавит вас от того, что где-то вы что-то упустили из вида, позволит вам "пощупать" проект ещё до того,как вы приступили к его реализвции, проанализировать его юзабилити. Спецификация - этого полная реализация вашего проекта псевдо-кодом - не экономьте время на её тщательную проработку.

2. Разработка компонентов.
    Реализуйте компоненты согласно составленной вами спецификации.
    Для добавления новых компонентов используйте скрипт manage.sh. После реализации вашего компонента не забудбте пересобрать вашу библиотеку компонентов (compile src/traliva_kit.pro). Для того, чтобы посмотреть, как отображается ваш компонент и как реагирует на изменение объекта состояния, откройте tests/index.html в браузере.

3. Разработка веб-прототипа (клиентской части без использования сервера).
    Согласно спецификации фрэймворка Тралива (см. traliva_doc/index.html) и спецификации вашего приложения, напишите ваше веб-приложение в отладочном режиме (slava_proj)
    Вместо реального API используйте заглушки (или веб-реализацию).

4. Реализуйте Низкоуровневый API на вашем веб-сервере (xxxx_proj_web).

Генерация проектов под PC-платформу и под android пока не реализована.

## Версионность

Определены даты, когда могут выходить новые версии фреймворка (или не выходить, если существенных нововведений не будет).

### traliva_doc:

Новые версии спецификации Тралива могут выходить не чаще, чем один раз в год - 1 марта каждого года может выходить новая версия спецификации. Версия спецификации Тралива обозначается одним числом - порядковым номером публикации.

### traliva:

Новые версии самого фреймворка Тралива могут выходить не чаще, чем один раз в три месяца. Версия фреймворка обозначается двумя числами - версией спецификации (которую реализует фреймворк) и номером выпуска в рамках спецификации.

### traliva_kit:

Базовый набор виджетов не имеет версий - он непрерывно меняется. Используйте скрипт для управления компонентами и механизмом тестирования компонентов, но сами компоненты следует рассматривать лишь как примеры реализации компонентов-виджетов - нужные вам виджеты разрабатываете только вы.


## Автор и лицензия

Copyright © 2017-2018 [Васильев Борис](https://github.com/1024sparrow)
Публикуется под лицензией [MIT license](https://github.com/1024sparrow/traliva/blob/master/LICENSE).
