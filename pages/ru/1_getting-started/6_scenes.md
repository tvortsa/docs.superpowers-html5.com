# Работа со сценами
Сцены позволяют визуально построить конфигурацию актеров и их компонентов (renderers, behaviors, etc.).

Мы собираемся восстановить наш фильм раньше, но использовать сцену вместо того, чтобы записывать их.

<div class="action">
  <p>Создайте новый ресурс сцены с именем `Main Scene` и откройте его.
</div>

<div class="note">
  <p>**В редакторе сцены, используйте `WASD`** чтобы двигаться вперед, назад, влево и вправо, «пробел», чтобы подняться, и «Shift», чтобы спуститься.
</div>

<div class="action">
  <p>Создайте actor с именем `Main Character` и разместите его в (0, 0, 0).  
  Добавьте ему компонент `Sprite Renderer` и задайте `Leonard` кв качестве используемого спрайта.  
  И еще один компонент, теперь уже типа `Behavior` и выберите `CharacterBehavior` как используемый класс.
</div>

<div class="action">
  <p>Нажмите в любом месте дерева сцены, чтобы отменить выбор актера, которого вы только что создали.
  Создайте другого актера с именем `Camera Man` и поместите его в (0, 0, 5).
  Добавьте компонент камеры на него.
</div>

<div class="note">
  <p>**Убедитесь что `Camera Man` actor не является родителем для `Main Character` actor** в дереве сцены.  
  Если это так, просто используйте drag'n'drop, чтобы очистить родительство.
</div>

Теперь, когда наша сцена готова, давайте вернемся к нашему скрипту. Мы можем избавиться от всего кода, который создали наши актеры, и вместо этого заменить его одной инструкцией для загрузки нашей сцены. Нам все еще нужно объявить `CharacterBehavior`.

<div class="action">
  <p>Замените содержимое скрипта `Game` следующим текстом:
</div>

```
class CharacterBehavior extends Sup.Behavior {
  update() {
    if (Sup.Input.isKeyDown("LEFT")) this.actor.move(-0.1, 0, 0);
    if (Sup.Input.isKeyDown("RIGHT")) this.actor.move(0.1, 0, 0);
  }
}
Sup.registerBehavior(CharacterBehavior);

Sup.loadScene("Main Scene");
```

<div class="note">
  <p>**Важно, чтобы вы объявили класс `CharacterBehavior` до того как загрузите сцену с помощью `Sup.loadScene`** (то есть выше, в сценарии), или Superpowers будет жаловаться, что он не знает (пока), каково поведение.
</div>

При работе с несколькими классами поведения для организационных целей обычно каждый из них помещается в отдельный сценарий. Поскольку сценарии будут читаться по порядку, убедитесь, что вы загружаете свою сцену в сценарий, размещенный под всеми сценариями поведения, которые он использует.

## Загрузка сцены при запуске игры без кода

Вы можете определить сцену, которая будет автоматически загружаться Superpowers после прочтения всех ваших сценариев в разделе «Игра» инструмента «Настройки».

![](http://i.imgur.com/DaWYJqS.png)

Это полностью эквивалентно вставке вызова в Sup.loadScene в конце вашего последнего скрипта, но это более удобно, так как вы всегда будете знать, где его изменить, если вам нужно.