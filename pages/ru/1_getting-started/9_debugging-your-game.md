# Отладка вашей игры

При использовании Superpowers из приложения, Вы можете открыть инструменты отладки, нажав на кнопку `Debug game` (или нажав `F6`). Большинство браузеров позволяют открывать похожие инструменты отладки, по клавише `F12` при запущенной игре.

Поскольку Superpowers app построен на NW.js, который основан на Chrome рантайм, встроенные средства отладки тоже есть в Chrome.

Две основные вкладки, которые вам понадобятся при запуске::

 * Вкладка `Console` , который предоставляет отчеты об ошибках во время выполнения и будет содержать результат любого вызова `Sup.log`.

 * Вкладка `Sources` , где вы найдете свои скрипты, а также весь движок, приводящий в действие вашу игру.

## Отладка и проверка состояния вашей игры

<div class="note">
  <p>Проверьте [этот обзор Chrome DevTools](https://developer.chrome.com/devtools) а также [это введение в отладку JavaScript](https://developer.chrome.com/devtools/docs/javascript-debugging). Не смотря на то что Superpowers на самом деле использует TypeScript, это надмножество JavaScript поэтому большая часть информации там должна применяться.
</div>

С открытым отладчиком вы можете использовать `Ctrl+P` и введите имя одного из ваших активов скрипта, чтобы перейти непосредственно к нему. [Поместите точку останова](https://developer.chrome.com/devtools/docs/javascript-debugging#add-remove-breakpoints) в методе `update` поведения, например, и ваша игра остановится, как только она снова достигнет этой строки.

При достижении точки останова на правой панели отобразится `Call Stack` (показывающий, как ваша игра достигла текущей функции / метода, например бредкрамбс) так же как `Scope Variables`, позволяя вам проверить содержимое всех доступных в настоящее время переменных.

`F10` позволяет сделать шаг вперед по одной инструкции за раз (полезно, если вы хотите проверить детали функции по одному шагу за раз), пока `F8` возобновит выполнение игры.

Вы можете захотеть [включить "Pause on uncaught exceptions"](https://developer.chrome.com/devtools/docs/javascript-debugging#pause-on-uncaught-exceptions) так что ваша игра автоматически остановится на определенной строке, возникнет ошибка во время выполнения и позволит вам проверить стек вызовов и состояние программы. Это действует только тогда, когда отладчик открыт.