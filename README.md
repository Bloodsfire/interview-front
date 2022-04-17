https://interview.cups.online/live-coding/

Вводная часть:
- рассказать немного о себе
- как пришли во фронт
- где работали до этого, какие проекты были, какие задачи решали
- отношение к верстке
- какие задачи хотелось бы решать, что нравится/не нравится в работе
- куда хочешь расти

Теория: <br>
База
- var, let, const
- типы в жсе
- == и ===
- {} == {}
- мутации, как склонировать глубокий объект
- ивент луп, промисы
- замыкание
- что такое this, отличие стрелочных функций от обычных
- Big O (сложность алгоритмов, минимальная теория), сложность метода arr.find(), сложность доступа к ключу объекта
- чистые функции (
  Примеры побочных эффектов:
  Видоизменение входных параметров
  console.log
  HTTP вызовы (AJAX/fetch)
  Изменение в файловой системе
  Запросы DOM)

Реакт <br>
https://webformyself.com/voprosy-na-sobesedovanie-po-react-redux/ <br>
https://github.com/likezninjaz/react-ru-interview-questions
- зачем нам нужен React и как вообще он работает(основная цель)
- что такое key и для чего он нужен в списках
- что таоке props.children
- Virtual-DOM что это и зачем
- React Hooks - что это, зачем это, отличие от классов
- Redux - что, зачем и для чего. Store, Action, Effect, Reducer
- JSX - что это и для чего

Практика:

https://codesandbox.io/s/event-loop-order-2cxkd5?file..

```javascript

// 0)
function test() {
    let a = 1;

    setTimeout(() => {
        a += 3;
        console.log("a: ", a);
      }, 0);

    let promise = new Promise((res, rej) => {
        a += 2;
        console.log("b: ", a);
        res(a);
    });

    promise
    .then((x) => {
        console.log("c: ", x);
        a += 1;
    })
    .catch(() => {
        console.log("d: ", a);
        a += 4;
    })
        .then(() => {
        console.log("e: ", a);
    });

    console.log("f: ", a);
}

test();

//b: 3
//f: 3
//c: 3
//e: 4
//a: 7

//b - создание промиса синхронное
//f - синхронная операция, тут все просто
//c - первый вызов промиса
//e - второй вызов промиса, но у нас был инкремент
//a - последней выполняется макротаск таймаута

_________________________________________________________________

// 1) реализовать функцию map(аналог метода Array.map)

const map = (arr, callback) => {
    // ...
}
const arr = [1,2,3,4,5]
console.log(map(arr, x => x * 10)) // [10,20,30,40,50]

_________________________________________________________________

// 2)
const makeCounter = () => {
// ...
};

const counter1 = makeCounter();
const counter2 = makeCounter();
console.log(counter1()); // 1
console.log(counter1()); // 2
console.log(counter2()); // 1
console.log(counter1()); // 3
console.log(counter2()); // 2

_________________________________________________________________

// 3)
const pipe = (...functions) => {
    // ...
}

console.log(pipe(
array => array[1],
number => number ** 2,
)([1, 2, 3])); // 4

// const pipe = (...functions) => (input) => functions.reduce((argument, func) => func(argument), input);

_________________________________________________________________

// 4)
const isAnagram = (str1, str2) => {
    // ...
}

isAnagram('Rosbank', 'Krabson'); // true
isAnagram('Rosbank', 'Société Générale'); // false 

_________________________________________________________________

// 5)
const max = (arr) => {
    // ...
}

const arr1 = [50, 1, 2, 3, 5, 30];
const arr2 = [-7, -13, -2, -43, -4];
const arr3 = [-1, 23, 0, -18, -37, 11];

console.log(max(arr1)) // 50
console.log(max(arr2)) // -2
console.log(max(arr3)) // 23

// arr.reduce((acc, cur) => cur > acc ? cur : acc, arr[0])

// let max = arr[0];

// arr.forEach(x => {
//     max = x > max ? x : max
// })

//
// for(i = 0; i < arr.length; i++) {
//   if(arr[i] > max) {
//     max = arr[i];
//   }
// }
```
