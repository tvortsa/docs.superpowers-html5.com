# Сценарий поведения

Поведение многократного использования может быть определено так, чтобы вы могли поместить их в нескольких актеров.
Вот как может выглядеть определение поведения:

```
class MyBehavior extends Sup.Behavior {
  // Объявите свойства здесь

  awake() {
    // Поместите логику инициализации здесь
    // this актер представляет собой актера, к которому привязано поведение
  }

  update() {
    // Поместите логику, которая должна выполняться здесь 60 раз в секунду
  }

}
// Не забудьте зарегистрировать свой класс поведения
Sup.registerBehavior(MyBehavior);
```

Внутри методов поведения (`awake`, `update` и другие, которые вы можете определить сами), Вы можете ссылаться на текущий компонент поведения с `this` и  actor котоорый с ним связан это `this.actor`.

Давайте добавим поведение к нашему главному герою из предыдущей главы.

<div class="action">
  <p>Вернитесь к вашему скрипту `Game` и добавьте следующий код в низ:
</div>

```
class CharacterBehavior extends Sup.Behavior {

  update() {
    if (Sup.Input.isKeyDown("LEFT")) {
      // Переместить актера текущего поведения на небольшое отрицательное смещение по оси X
      this.actor.move(-0.1, 0, 0);
    }

    if (Sup.Input.isKeyDown("RIGHT")) {
      // То же, но положительным значением, чтобы идти направо
      this.actor.move(0.1, 0, 0);
    }
  }

}
Sup.registerBehavior(CharacterBehavior);

// Как только класс поведения определен,
// нам нужно прикрепить его к нашему персонажу
mainCharacterActor.addBehavior(CharacterBehavior);
```

`Sup.Input.isKeyDown(...)` возвращает `true` только когда указанная клавиша нажата.

<div class="note">
  **Есть много других функций** доступных для чтения ввода от игрока и реакции на него.  
  Все они перечислены в **TypeScript <abbr title="Application Programming Interface">API</abbr> browser** доступном изнутри Superpowers.
</div>