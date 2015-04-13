﻿# Отладка #

При загрузке приложение iikoFront выполняет поиск плагинов и для каждого из них запускает процесс-контейнер `Resto.CashServer.OutOfProcHost.exe`, в контексте которого плагин и будет работать. При всех своих эксплуатационных преимуществах этот подход создаёт ряд неудобств на этапе отладки:

- не подключается автоматически отладчик Visual Studio (не работают breakpoints),
- после каждой остановки плагина и внесения исправлений необходимо перезапускать приложение iikoFront (долго).

Впрочем, эти недостатки не являются непреодолимыми, в одной из следующих версий будет предложено решение для более удобной отладки. Пока же рекомендуется свести неудобства к минимуму следующим образом:

- В Visual Studio в настройках проекта на вкладке `Build` в разделе `Output` указать в качестве `Output path` путь к папке с плагинами приложения iikoFront. Благодаря этому после каждой сборки плагин сразу будет публиковаться в эту папку, его не придётся копировать вручную.
- В Visual Studio в настройках проекта на вкладке `Debug` в разделе `Start Action` выбрать пункт `Start external program` и указать путь к исполняемому файлу `iikoFront.Net.exe`. В совокупности с предыдущим пунктом это позволит одним нажатием F5 (`Debug → Start Debugging`) скомпилировать плагин, скопировать его в папку с плагинами и запустить iikoFront.
- В начале метода `Init` плагина добавить вызов `Debugger.Launch()`, чтобы получать предложение подключить отладчик. Можно, конечно, подключить его самому, выбрав в меню `Debug → Attach to Process`, но это потребует больше кликов, кроме того, придётся выбирать из нескольких процессов-контейнеров с одинаковым названием.