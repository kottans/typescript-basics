
### Intro

Для первого знакомства с ТайпСкриптом мы постараемся как можно меньше заниматься настройкой окружения - мы разберемся с этим позже. На первом занятии наша задача - понять, что такое ТайпСкрипт и какие проблемы он решает (а какие - нет). Поэтому мы будем работать в TypeScript Playground и локально в заранее настроенном проекте.

TypeScript boilerplate project - TODO

Superset of JS
Надмножестве Джаваскрипта (всякий валидный тайпскрипт есть джаваскрипт, обратное неверно)

Термины:
subset vs superset

Какую проблему решает ТайпСкрипт?
В Джаваскрипте все же были инструменты, которые позволяли анализировать код на стадии написания (еслинт), но их возможностей было недостаточно.
Что делает тайпскрит? Очень грубо, компилятор тайпскрипта получает от вас информацию о типах и проходит все возможные ветки выполнения вашего кода с точки зрения типов и проверяет, что на уровне типов не произойдет ошибки.

Почему мы вообще привязались к типам и зачем нам это нужно?
тип в понимании тайпскрипта описывает форму (shape) переменной.
Что такое type error

Какие самые частые type error вам встречались?

тип - это в первую очередь определенное поведение (например, определенные на объекте определенного типа методы).

Где тайпскрипт не  может нам помочь?
Он органичен теми знаниями, которые получает от нас. В частности, ему приходится рассчитывать на нас, чтобы узнать типы значений, приходящих извне (самый яркий пример - ответ от АПИ)

Важно: тайпскрипт работает только до стадии компиляции включиьтельно: как только тайпскрипт скомпилировался в джаваскрипт, он больше ничего для вас сделать не сможет: он не выполняется в рантайме.

Статический анализ кода позволяет до исполнения кода выявить некоторые ошибки. JavaScript - динамически типизированный язык. В нем есть типы, но они присваиваются значениям, а не переменным. ТайпСкрипт позволяет обеспечить статическую типизацию, то есть, привязать тип к переменной и проверить сходимость типов до выполнения, на стадии компиляции. Это допускается при помощи аннотаций типов. Синтаксис рассмотрим позже, но вот небольшой пример:

Где писать типы? Что именно типизировать?
Типы определяются там, где есть интерфейс (взаимодействие). Например, тип параметров функции и тип возвращаемого значения. 

На первом этапе можно рассматривать как помощник, который ограничивает вас, чтобы уберечь от ошибок


Как работает под капотому (компиляция в джаваскрипт. Часть кода тайпскрипта остается в получившемся джаваскрипте, другая исчезает бесследно)
требует компиляции (компилируется в джавасрикпт). Пример в песочнице TODO

Синтаксис: type annotations

Почему ТайпСкрипт может раздражать:
(пример с undefined, когда мы уверены, что все ок)

Начнем с упражнения. Этот код не компилируется. Попробуйте исправить ситуацию. Внимательно прочтите ошибки, которые показывает вам ТайпСкрипт и попробуйте исправить.

https://www.typescriptlang.org/play/#code/PQKhCgAIUhRANAggWQAoBlaQIxRnyAFQAsBTSAMwFcA7AYwBcBLAexsgGdiWqAbAE0i8WAc0hUOpAE6QaAQwC25Bi0h02HFr1IA6SADEmAD0gMAngAdy0qSykcdeYOHDqaHBuMkyAvJADeUJDB8koAXJAA5ABSLMQ0keAAvgDcLtT0zGxCogCq3gByiqQAFKGkER5STDQiAJQRAG4sTIKBwcFumto6wiIlAAb50pEcssWQTBwRACT+5UkDdWmpLn3DUkVKJRLSyy4uoBDQcEhomJAATAQEAOrkNKSkgipqcrx0fHIMyiwM75AWBRIO9eF5pJMaBYqAwHAR0KQGKMQRwOFQlKYyJQtMIAO41MQAEQA8shOAwpFRGFQpBUCAAeGrQzzmKw+ABENHRACNpOyAHw3E6GEys6xSWz2RzQZzgbQsv4AvwABjSXU8TJhkD8-BYnyUNAYOgAjlRpGYAMqkbSMOz0gAShGQ6AAklCYbBtAaGPySpFNUj9kFggGdHJ+PxYI1SIb0FMfo8pH66MQ5LVSJEADSQEoVODRw11bX8gLBjrBFT-MEAaj8JQdTtd7oYntI3v5un+UhEiLqOka7zNKyAA

```typescript
/**
 * EXAMPLE 1
 * 
 * The function should log user name to console. Fix type errors.
 */

const user = {
    name: 'John'
};

function logUserName(name: string): void {
    console.log(`User's name is: ${name}`);
};

logUserName(user);



/**
 * EXAMPLE 2
 * 
 * We need to calculate total of all user inputs.
 * Let's assume the following DOM structure:
 * <input type="number">
 * 
 * Fix type errors.
 */

let total = 0;
const input = document.querySelector<HTMLInputElement>('input');

input.addEventListener('change', (e: Event) => {
    total += (<HTMLInputElement>e.target).value;
}

/**
 * EXAMPLE 3
 * 
 * Fix type errors
 */


setTimeout(console.log('this will be logged after 1 second'), 1000);
```

А теперь попробуем написать типы самостоятельно. В этом упражнении ТайпСкрипт подчеркивает, где не хватает типов. Добавьте их.

// TODO


Выведение типов (Type Inference)

ТайпСкрипт умеет выводить типы: если компилятор может сделать однозначное предположение о том, какой тип ожидается, тип можно не указывать. Рассмотрим пример. В этом коде мы определили только тип User и указали значение, принимаемое функциями на вход. 

https://www.typescriptlang.org/play/index.html?ssl=19&ssc=15&pln=19&pc=26#code/GYVwdgxgLglg9mABAcwKZQKoGdUCcCCaAFCDrgFyIDeiAhmpWCALYBGeAvgJTUBQiAxLnQhcSUngB09VAG5eHeVACeAB1SJseRAF4+gug0RM2eeQbC1mqSlii4YYZPI68ICO4gm4slLbgBtAF1dRAD+QSoIgwFLa0oAcgApOAALMASAGmiYmUoAJgAGHI5sgyiYwTibRGTaMFQsnIM8xHyARhLeIPlebyxJYQATEAhUIiIoOChaABtMrzIeHQA+RCmZ2cQAahR0f0Jx7y4Fwq5e0EhYBER3cEwyQ4AVabmSMl9NMmCeCsFZ9DrV5bPSFcyCfqSYBwXAAUVoEFS720qyBmx2ejQDzwh2RuC45xywigoiQGzmLiAA

```typescript
function getUserAge(user: { age: number}) {
    return user.age;
};
type User = {
    age: number;
    name: string;
}

users.reduce((total, user) => total + getUserAge(user), 0);

function countUserAgeTotal(users: User[]) {
    let total = 0;
    users.forEach(user => total += getUserAge(user));
    return total;
}

```

Откройте файл в редакторе или ссылку на песочницу и посмотрите, какие типы имеют переменные getUserAge, countUserAgeTotal (для этого нужно навести курсор на имя переменной). Посмотрите, какие предположения ТайпСкрипт делает о типах там, где они не указаны явно.