# Powerformer JavaScript Style Guide() {

*A mostly reasonable approach to Coding*

> **注意**: 一般的变量命名会以涵盖标题为主，涉及四个值得变量命名会使用`top, right, bottom, left`, 涉及少于四个或者大于四个的变量命名会使用`first, second ...`。

## 目录 <a id="table-of-contents"></a>

  1. [代码风格](#code-style)
  2. [字符串](#Strings)
  3. [解构赋值](#Destructuring)
  4. [对象](#Objects)
  5. [数组](#Arrays)
  6. [函数](#Functions)
  7. [类](#Classes)
  8. [模块](#Modules)

## 代码风格 <a id="code-style"></a>

  - [1.1](#code-style-indent) 语句块内每行代码缩进`2`个空格。

    ```javascript
    // bad
    function heros() {
        if (x) {
            return x;
        } else {
            return y;
        }
    }

    // good
    function heros() {
      if (x) {
        return x;
      } else {
        return y;
      }
    }
    ```
    
  - [1.2](#code-style-limit-row) 每行代码不超过`119`个字符。

    ```javascript
    // bad
    const myBadDream = "Lorem ipsum dolor sit amet consectetur adipisicing elit. Officiis dicta maxime at ratione assumenda, quos, asperiores odit deleniti quia quidem atque quo tempore error a nihil impedit excepturi aliquid nemo?";

    // good
    const myGoodDream = "Lorem ipsum dolor sit amet consectetur adipisicing elit. \
                Officiis dicta maxime at ratione assumenda, quos, asperiores odit \
                deleniti quia quidem atque quo tempore error a nihil impedit      \
                excepturi aliquid nemo?";
    ```

**[⬆ back to top](#table-of-contents)**
  
## 字符串 <a id="Strings"></a>

  - [2.1](#string-quote-style) 静态字符串一律使用单引号，不使用双引号。动态字符串使用反引号。

    ```javascript
    // bad
    const staticString = "foobar";

    // good
    const staticString = 'foobar';
    const dynamicString = `foo${staticString}bar`;
    ```

**[⬆ back to top](#table-of-contents)**

## 解构赋值 <a id="Destructuring"></a>

  - [3.1](#destructuring-array) 使用数组成员对变量赋值时，优先使用解构赋值。

    ```javascript
    const arr = [1, 2, 3, 4];

    // bad
    const desArrFirst = arr[0];
    const desArrSecond = arr[1];

    // good
    const [desArrFirst, desArrSecond] = arr;
    ```

  - [3.2](#destructuring-func-params) 函数参数如果是对象成员，优先使用解构赋值

    ```javascript
    // bad
    function getDream(pfPartner) {
      const firstDream = pfPartner.firstDream;
      const secondDream = pfPartner.secondDream;
    }

    // good
    function getDream(pfPartner) {
      const { firstDream, secondDream } = pfPartner;
    }

    // also good
    function getDream({ firstDream, secondDream }) {
      
    }
    ```

  - [3.3](#destructuring-func-return) 如果函数返回多个值，优先使用对象的解构赋值，而不是数组的解构赋值。这样便于以后添加返回值，以及更改返回值的顺序。

    ```javascript
    // bad
    function processInput(input) {
      return [left, right, top, bottom];
    }

    // good
    function processInput(input) {
      return { left, right, top, bottom };
    }

    const { left, right } = processInput(input);
    ```

**[⬆ back to top](#table-of-contents)**

## 对象 <a id="Objects"></a>

  - [4.1](#object-define-comma) 单行定义的对象，最后一个成员不以逗号结尾。多行定义的对象，最后一个成员以逗号结尾。

    ```javascript
    // bad
    const objComma1 = { first: value1, second: value2, };
    const objComma2 = {
      first: value1,
      second: value2
    };

    // good
    const objComma1 = { first: value1, second: value2 };
    const objComma2 = {
      first: value1,
      second: value2,
    };
    ```

  - [4.2](#object-staticable) 对象要静态化，一旦定义，就不得改变，如果要改变，使用`Spread Syntax '...'`来返回一个新对象。

    ```javascript
    // bad
    const staticObj = {};
    staticObj.first = 3;

    // also bad
    const staticObj = { first: 2 };
    staticObj.first = 3;

    // good
    const staticObj = { first: 2 };
    const nextStaticObj = { ...staticObj, first: 3};

    // also good
    const staticObj = { first: 2 };
    const nextStaticObj = { ...staticObj, first: 3};
    ```

  - [4.3](#object-prop-expression) 如果对象的属性名是动态的，使用属性表达式来定义。

    ```javascript
    function getKey(condition) {
      ...
      return result;
    }

    const propExpObj = {
      first: 'pftom',
      [getKey('enabled')]: true,
    };
    ```

  - [4.4](#object-simplify-expression) 对象的属性和方法都要采用简洁表达式。

    ```javascript
    // bad
    const simpExpObj1 = {
      first: first,
    };

    // also bad
    const simpExpObj2 = {
      addFirst: function (value) {
        ...
        return result;
      }
    }

    // good
    const simpExpObj1 = {
      first,
    };

    // also good
    const simpExpObj2 = {
      addFirst(value) {
        ...
        return result;
      },
    };
    ```

**[⬆ back to top](#table-of-contents)**

## 数组 <a id="Arrays"></a>

  - [5.1](#array-copy) 拷贝数组使用 `Spread Syntax '...'` 。

    ```javascript
    // bad
    const items = [1, 2, 3, 4];
    const copyItems = [];
    let i;
    for (i = 0; i < items.length; i++) {
      copyItems[i] = items[i];
    }

    // good
    const items = [1, 2, 3, 4];
    const copyItems = [ ...items ];
    ``` 
  
  - [5.2](#array-change) 使用 `Array.from` 将类数组对象转换为数组。

    ```javascript
    const analogyArrObj = document.querySelectorAll('.nodes');
    const arr = Array.from(analogyArrObj)
    ```

**[⬆ back to top](#table-of-contents)**

## 函数 <a id="Functions"></a>

  - [6.1](#function-arrow) 能使用箭头函数尽量使用箭头函数。简洁而且可以绑定`this` 。

    ```javascript
    // bad
    const items = [1, 2, 3];
    items.map(function (item) {
      return item * item;
    });

    // good single line statments
    const items = [1, 2, 3];
    items.map(item => item * item);

    // also good multiline statements
    const items = [1, 2, 3];
    items.map((item) => {
      ...
      return item * item;
    })
    ```

  - [6.2](#function-arguments) 不要使用 `arguments`， 使用 `rest '...'` 运算符来替代。 `arguments` 是类数组， 而 `rest` 是真的数组。

    ```javascript
    // bad
    function concatenateAll() {
      const args = Array.prototype.slice.call(arguments);
      return args.join('');
    }

    // good
    function concatenateAll(...args) {
      return args.join('');
    }
    ```

  - [6.3](#function-default-syntax) 使用默认值语法来设置函数参数的默认值。

    ```javascript
    // bad
    function setDefault(opts) {
      opts = opts || {};
      ...
    }

    // good
    function setDefault(opts = {}) {
      ...
    }
    ```

**[⬆ back to top](#table-of-contents)**

## 类 <a id="Classes"></a>

  - [7.1](#class-prototype) 在需要使用  `Prototype` 的操作时，都用 `Class` 来取代。

    ```javascript
    // bad
    function Queue(contents = []) {
      this._queue = [...contents];
    }

    Queue.prototype.pop = function () {
      const value = this._queue[0];
      return value;
    }

    // good
    class Queue {
      constructor(contents = []) {
        this._queue = [ ...contents ];
      }

      pop () {
        const value = this._queue[0];
        return value;
      }
    }
    ```

**[⬆ back to top](#table-of-contents)**

## 模块 <a id="Modules"></a>

  - [8.1](#module-import) 使用 `import` 代替 `require` 。
  
    ```javascript
    // bad
    const moduleA = require('moduleA');
    const { firstFunc, secondFunc } = moduleA;

    // good
    import { firstFunc, secondFunc } from 'moduleA';
    ```

  - [8.2](#module-export) 使用 `export` 代替 `module.exports` 。

    ```javascript
    // bad
    class moduleA {
      ...
    }

    module.exports = moduleA;

    // good

    class moduleA {
      ...
    }

    export default moduleA;
    ```

  - [8.3](#module-export-&default) `export default` 与 `export` 不要同时使用。

    ```javascript
    // bad
    export function myFunc () {
      ...
    }

    const value = 2;
    export default value;

    // good
    const value = 2;
    export default value;

    // also good
    function myFunc1 () {
      ...
    }

    function myFunc2 () {

    }

    export {
      myFunc1,
      myFunc2,
    }
    ```

  - [8.4](#module-default) 不要在模块中使用通配符，如果要输出多个模块，使用 `export default`

    ```javascript
    // bad
    import * as myModule from './myModule';

    // good
    export default {
      moduleA,
      moduleB,
    }
    import myModule from './myModule';
    ```

  - [8.5](#module-function) 如果默认输出的是函数，那么函数名首字母需要小写。
  
    ```javascript
    // bad
    function MyFunc () {
      ...
    }

    export default MyFunc;

    // good
    function myFunc () {
      ...
    }

    export default myFunc;
    ```

  - [8.6](#module-class) 如果默认输出的是对象，那么对象名首字母要大写。

    ```javascript
    // bad 
    const myObj = {
      ...
    };

    export default myObj;

    // good
    const MyObj = {
      ...
    };
    
    export default MyObj;
    ```

**[⬆ back to top](#table-of-contents)**

# };