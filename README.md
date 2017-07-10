# 驴妈妈H5开发规范

**本规范的主要目标**：

* 代码风格一致

  通过保持代码风格的一致，使代码具有良好的可读性，降低代码的维护成本，提高团队间的协作效率。

* 最佳实践

  通过遵守最佳实践，可以降低bug引入的可能，提高页面性能，编写出可扩展可维护的代码。

**本规范的编写原则**：努力兼顾代码风格与开发效率的平衡，既要努力做到 “使每一行代码都像是同一个人编写的”，又要尽量避免 “大家都觉得这样很麻烦”。

**本规范的更新**：本规范是当前阶段的一个总结，不是最终版，也不会有最终版，随着代码风格的优化、最佳实践的发展，本规范也会变化。

**本规范的代码说明**：不符合规范的代码写法，会有注释 `// 不好`，符合规范的代码写法，会有注释 `// 好`，最佳写法，会有注释 `// 最佳`；在空格相关的规范中，使用 `·` 号来强调表示空格。

### **规范最重要的是执行。**

## 目录

* [JavaScript](#javascript)
    * [命名](#命名)
    * [空格](#空格)
    * [逗号](#逗号)
    * [分号](#分号)
    * [变量](#变量)
    * [字符串](#字符串)
    * [对象](#对象)
    * [数组](#数组)
    * [函数](#函数)
    * [箭头函数](#箭头函数)
    * [类](#类)
    * [属性](#属性)
    * [模块](#模块)
    * [迭代器](#迭代器)
    * [条件语句](#条件语句)
    * [运算符](#运算符)
    * [类型转换](#类型转换)
    * [注释](#注释)
* [HTML](#html)
* [CSS](#css)
* [性能相关](#性能相关)
* [业务相关](#业务相关)

## JavaScript

### 命名

* 避免使用单一字母命名，让你的名字具有实际含义。

    ```js
    // 不好
    function q() {
        // ...
    }

    // 好
    function query() {
        // ...
    }
    ```
* 使用 [小驼峰命名法](https://zh.wikipedia.org/wiki/%E9%A7%9D%E5%B3%B0%E5%BC%8F%E5%A4%A7%E5%B0%8F%E5%AF%AB) 来命名基本类型、对象和函数。

    ```js
    // 不好
    const this_is_my_object = {};
    function c() {}

    // 好
    const thisIsMyObject = {};
    function thisIsMyFunction() {}
    ```

* 使用 [Pascal命名法](https://zh.wikipedia.org/wiki/%E5%B8%95%E6%96%AF%E5%8D%A1%E5%91%BD%E5%90%8D%E6%B3%95) 来命名构造函数和类。

    ```js
    // 不好
    function user(options) {
        this.name = options.name;
    }

    const bad = new user({
        name: 'Jack',
    });

    // 好
    class User {
        constructor(options) {
            this.name = options.name;
        }
    }

    const good = new User({
        name: 'Jack',
    });
    ```

* 缩略词应该保持全部大写或者全部小写。

    ```js
    // 不好
    import SmsContainer from './containers/SmsContainer';

    // 不好
    const HttpRequests = [
        // ...
    ];

    // 好
    import SMSContainer from './containers/SMSContainer';

    // 好
    const HTTPRequests = [
        // ...
    ];
    ```

### 空格

* 将 Tab 设置为 4 个空格。

    > 主流的编辑器一般都支持设定 Tab 对应的空格数，以 Visual Studio Code 为例，设置方式：点击文件 -> 首选项 -> 设置，搜索 "editor.tabSize"。

    ```js
    // 不好
    function foo() {
    ∙let name;
    }

    // 不好
    function bar() {
    ∙∙let name;
    }

    // 好
    function foo() {
    ∙∙∙∙let name;
    }
    ```

* 不要混用 Tab 和空格。

    > 这可能会导致一些格式上的异常，例如：在 Jade 中混用 Tab 和空格就会出错。

* 在左大括号之前加 1 个空格。

    ```js
    // 不好
    function test(){
        console.log('test');
    }

    // 好
    function test()∙{
        console.log('test');
    }
    ```

* 在流程控制语句（如 `if`, `while` 等）的左小括号之前加 1 个空格。

    ```js
    // 不好
    if(true) {
        done();
    }

    // 好
    if∙(true) {
        done();
    }
    ```

* 将 `else` 放在与前面 `}` 同一行并加 1 个空格。

    ```js
    // 不好
    if (true) {
        // ...
    }else {
        // ...
    }

    // 不好
    if (true) {
        // ...
    }
    else {
        // ...
    }

    // 好
    if (true) {
        // ...
    }∙else {
        // ...
    }
    ```

* 在函数的定义和调用中，函数名与参数列表之间不要有空格。

    ```js
    // 不好
    function test∙() {
        console.log∙('test');
    }

    // 好
    function test() {
        console.log('test');
    }
    ```
* 运算符之间使用空格隔开。

    ```js
    // 不好
    const x=y+5;

    // 好
    const x∙=∙y∙+∙5;
    ```

* 在文件的末尾加上一行空白行。

    ```js
    // 不好
    import { es6 } from './test';
        // ...
    export default es6;
    ```

    ```js
    // 不好
    import { es6 } from './test';
        // ...
    export default es6;↵
    ↵
    ```

    ```js
    // 好
    import { es6 } from './test';
        // ...
    export default es6;↵
    ```

* 多个方法（大于 2 个）形成的方法链调用，从第 1 或第 2 个方法开始换行调用，并将 `.` 号置于行首以说明该行是方法调用，而不是开始一个新的语句。

    ```js
    // 好
    const result1 = data.replace('[str1]', 'str1').replace('[str2]', 'str2');

    // 不好
    const result2 = data.replace('[str1]', 'str1').replace('[str2]', 'str2').replace('[str3]', 'str3');

    // 好
    const result3 = data
        .replace('[str1]', 'str1')
        .replace('[str2]', 'str2')
        .replace('[str3]', 'str3');

    // 好
    const result4 = data.replace('[str1]', 'str1')
        .replace('[str2]', 'str2')
        .replace('[str3]', 'str3');
    ```

* 不要在语句块的开始和结尾处放置空行。

    ```js
    // 不好
    function bar() {

        console.log(foo);

    }

    // 好
    function bar() {
        console.log(foo);
    }
    ```

* 不要在小括号内的两侧放置空格。

    ```js
    // 不好
    function bar(·foo·) {
        return foo;
    }

    // 好
    function bar(foo) {
        return foo;
    }

    // 不好
    if (·foo·) {
        console.log(foo);
    }

    // 好
    if (foo) {
        console.log(foo);
    }
    ```

* 不要在中括号内的两侧放置空格。

    ```js
    // 不好
    const foo = [·1, 2, 3·];
    console.log(foo[·0·]);

    // 好
    const foo = [1, 2, 3];
    console.log(foo[0]);
    ```

* 在大括号内的两侧放置空格。

    ```js
    // 不好
    const person = {name: 'Kathy'};

    // 好
    const person = {·name: 'Kathy'·};
    ```

* 对象的键和冒号间不加空格，冒号和值间加空格。

    ```js
    // 不好
    const foo = {
        key1∙:∙value1,
        key2:value2,
        key3∙:value3
    };

    // 好
    const foo = {
        key1:∙value1,
        key2:∙value2,
        key3:∙value3
    };
    ```

* 逗号之前不加空格，逗号之后加空格。

    ```js
    // 不好
    const foo = 1,bar = 2;
    const arr = [1∙,2];
    const obj = {"foo": "bar"∙,∙"baz": "qur"};
    foo(a,b);
    new Foo(a∙,b);
    function foo(a∙,∙b){}
    a,b

    // 好
    const foo = 1,∙bar = 2;
    const arr = [1,∙2];
    const obj = {"foo": "bar",∙"baz": "qur"};
    foo(a,∙b);
    new Foo(a,∙b);
    function foo(a,∙b){}
    a,∙b
    ```

* 在注释内容之前加 1 个空格。

    ```js
    // 不好
    //这里控制是否有效
    const active = true;

    // 好
    //∙这里控制是否有效
    const active = true;

    // 不好
    /**
    *make() 返回一个新的元素
    *基于传进来的标签名称
    */
    function make(tag) {

        // ...

        return element;
    }

    // 好
    /**
    *∙make() 返回一个新的元素
    *∙基于传进来的标签名称
    */
    function make(tag) {

        // ...

        return element;
    }
    ```

### 逗号

* 不要将逗号放在前面。

    ```js
    // 不好
    const story = [
          once
        , upon
        , aTime
    ];

    // 好
    const story = [
        once,
        upon,
        aTime,
    ];
    ```

* 多行情况下，建议在最后一行的参数或属性的末尾添加一个额外逗号。

    > 这会方便你新增或删除项，并让 git 的差异列表更清晰。

    ```diff
    // 不好 - 事实上只新增了一个属性，但 git 差异列表会显示有 3 行改动
    const hero = {
         firstName: 'Florence',
    -    lastName: 'Nightingale'
    +    lastName: 'Nightingale',
    +    inventorOf: ['coxcomb chart', 'modern nursing']
    };

    // 好 - git 差异列表会展示 1 行改动
    const hero = {
         firstName: 'Florence',
         lastName: 'Nightingale',
    +    inventorOf: ['coxcomb chart', 'modern nursing'],
    };
    ```

    ```js
    // 不好
    const hero = {
        firstName: 'Dana',
        lastName: 'Scully'
    };

    const heroes = [
        'Batman',
        'Superman'
    ];

    // 好
    const hero = {
        firstName: 'Dana',
        lastName: 'Scully',
    };

    const heroes = [
        'Batman',
        'Superman',
    ];

    // 不好
    function createHero(
        firstName,
        lastName,
        inventorOf
    ) {
        // does nothing
    }

    // 好
    function createHero(
        firstName,
        lastName,
        inventorOf,
    ) {
        // does nothing
    }

    // 好（注意：可变参数后面不可以有逗号）
    function createHero(
        firstName,
        lastName,
        inventorOf,
        ...heroArgs
    ) {
        // does nothing
    }

    // 好（因为该条规则仅适用于多行）
    function createHero(firstName, lastName, inventorOf) {
        // does nothing
    }
    ```

### 分号

* 语句的结尾处必须要有分号。

    ```js
    // 不好
    const name = 'ESLint'

    object.method = () => {
        // ...
    }

    // 好
    const name = 'ESLint';

    object.method = () => {
        // ...
    };
    ```

### 变量

* 总是使用 `const` 来定义常量，避免使用 `var`。

    > 这能够确保你无法对变量重新赋值，在开发阶段就发现可能的问题。
    
    ```js
    // 不好
    var num1 = 1;
    var num2 = 2;

    // 好
    const num1 = 1;
    const num2 = 2;
    ```

* 如果你需要为引用重新赋值，使用 `let` 而不是 `var`。

    > `let` 是块作用域，`var` 是函数作用域。

    ```js
    // 不好
    var count = 1;
    if (true) {
        count += 1;
    }

    // 好
    let count = 1;
    if (true) {
        count += 1;
    }

    // 不好
    for (var i = 0; i < 3; i++) {
        // ...
    }

    // 好
    for (let i = 0; i < 3; i++) {
        // ...
    }
    ```
* 请注意：`let` 和 `const` 都是块级作用域。

    ```js
    // const 和 let 只存在于它们被定义的区块内。
    {
        let a = 1;
        const b = 1;
    }

    // 引用错误：a未定义
    console.log(a); 

    // 引用错误：b未定义
    console.log(b); 
    ```

* 变量声明不要省略关键字。

    ```js
    // 不好
    cat = new Cat();

    // 好
    const cat = new Cat();

    // 好
    window.cat = new Cat();
    ```

* 不要使用链式声明。

    > 链式声明会创建隐式全局变量，可能引入 bug。

    ```js
    // 不好
    (function example() {
        /**
        * JavaScript 会将这行代码解析为：
        * let a = (b = (c = 1));
        * let 关键字仅作用于变量 a，变量 b 和 c 将定义于全局作用域。
        */
        let a = b = c = 1;
    }());

    // 出错：a 未定义
    console.log(a); 

    // 输出 1
    console.log(b);

    // 输出 1
    console.log(c); 

    // 好
    (function example() {
        let a = 1;
        let b = a;
        let c = a;
    }());

    // 出错：a 未定义
    console.log(a); 

    // 出错：b 未定义
    console.log(b); 

    // 出错：c 未定义
    console.log(c); 
    ```

### 字符串

* 字符串使用单引号 `''` 。

    ```js
    // 不好
    const name = "Kathy";

    // 不好 - 仅当字符串中需要插入变量或换行时才使用模板字符串
    const name = `Kathy`;

    // 好
    const name = 'Kathy';
    ```

* 对于长字符串不要人为分割。

    > 很多规范都不允许字符串过长，推荐进行字符串拼接分割，但事实上，长字符串分割之后将难以维护，并可能导致关键字搜索无效（关键字被分割了）；而长字符串难以阅读的问题，使用现代编辑器就可以解决，以 Visual Studio Code 为例：点击查看 -> 切换自动换行。

    ```js
    // 不好
    const errorMessage = 'This is a super long error that was thrown because ' +
    'of Batman. When you stop to think about how Batman had anything to do ' +
    'with this, you would get nowhere fast.';

    // 不好
    const errorMessage = 'This is a super long error that was thrown because \
    of Batman. When you stop to think about how Batman had anything to do \
    with this, you would get nowhere \
    fast.';

    // 好
    const errorMessage = 'This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.';
    ```

* 构建包含变量或换行的字符串时，使用模板字符串而不是字符串拼接。

    ```js
    // 不好
    function sayHi(name) {
        return 'How are you, ' + name + '?';
    }

    // 不好
    function sayHi(name) {
        return ['How are you, ', name, '?'].join();
    }

    // 好
    function sayHi(name) {
        return `How are you, ${name}?`;
    }
    ```

* 不要对字符串使用 `eval()` 方法，它可能会导致很多漏洞。

    ```js
    // 不好
    var result = eval('(function() { const a = 1; return a; }());');
    ```

* 避免无意义的转义符 `\`。

    > 转义符会降低可读性，应该仅在必要时才存在。

    ```js
    // 不好
    const foo = '\'this\' \i\s \"quoted\"';

    // 好 - 仅 this 前后的引号才需要转义
    const foo = '\'this\' is "quoted"';
    ```

### 对象

* 使用简洁语法创建对象。

    ```js
    // 不好
    const item = new Object();

    // 好
    const item = {};
    ```

* 使用对象方法的简写。

    ```js
    // 不好
    const atom = {
        value: 1,

        addValue: function (value) {
            return atom.value + value;
        },
    };

    // 好
    const atom = {
        value: 1,

        addValue(value) {
            return atom.value + value;
        },
    };
    ```

* 使用属性值的简写。

    ```js
    const name = 'Kathy';

    // 不好
    const obj = {
        name: name,
    };

    // 好
    const obj = {
        name,
    };
    ```

* 仅在无效的属性名上加引号。

    > 一般来说，我们认为这在主观上更容易阅读。它改进了语法高亮，并且更容易被许多JS引擎优化。

    ```js
    // 不好
    const bad = {
        'foo': 3,
        'bar': 4,
        'data-blah': 5,
    };

    // 好
    const good = {
        foo: 3,
        bar: 4,
        'data-blah': 5,
    };
    ```

* 不要直接使用 `Object.prototype` 上的方法，例如 `hasOwnProperty`，`isPrototypeOf` 等。

    > 这些方法可能会被对象的自定义属性覆盖，例如对象：`{hasOwnProperty: false}`，或者当该对象的 `__proto__` 属性为 `null` 时，例如使用 `Object.create(null)` 创建的对象，就不存在这些方法。

    ```js
    // 不好
    console.log(obj.hasOwnProperty(key));

    // 好
    console.log(Object.prototype.hasOwnProperty.call(obj, key));
    ```

### 数组

* 使用简洁语法创建数组。

    ```js
    // 不好
    const items = new Array();

    // 好
    const items = [];
    ```

* 使用 [Array#push](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/push) 在数组末尾添加元素。

    ```js
    const someStack = [];

    // 不好
    someStack[someStack.length] = 'abc';

    // 好
    someStack.push('abc');
    ```

* 使用 [扩展运算符](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Spread_operator) `...` 来复制数组。

    > 注意：这些示例写法都是浅拷贝，不是深拷贝。

    ```js
    const items = [1, 2, 3];

    // 不好
    const itemsCopy = [];
    for (let i = 0; i < items.length; i++) {
        itemsCopy[i] = items[i];
    }

    // 好
    const itemsCopy = items.slice();

    // 好
    const itemsCopy = Array.from(items);

    // 最佳
    const itemsCopy = [...items];
    ```

* 使用 [Array.from](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/from) 将类数组对象（arguments、NodeList 等）转换为标准数组。

    ```js
    // 不好
    const divs = Array.prototype.slice.call(document.querySelectorAll('div'));

    // 好
    const divs = Array.from(document.querySelectorAll('div'));

    // 好
    function something() {
        var args = Array.from(arguments);
        // ...
    }
    ```

### 函数

* 不要在非函数代码块（`if`、`while` 等）的内部定义函数。

    ```js
    // 不好
    if (true) {
        function test() {
            console.log(111);
        }
        // ...
    }

    // 好
    let test;
    if (true) {
        test = () => {
            console.log(111);
        };
        // ...
    }
    ```

* 将自执行函数用括号包起来。

    ```js
    // 不好
    var x = function() {
        console.log(1); 
    }();

    // 不好
    (function() {
        console.log(1); 
    })();

    // 好
    (function() {
        console.log(1); 
    }());
    ```

* 不要将参数命名为 `arguments`，这将覆盖掉传入函数作用域的 `arguments` 对象。

    ```js
    // 不好
    function foo(arguments) {
        // ...
    }

    // 好
    function foo(args) {
        // ...
    }
    ```

* 不要使用 `arguments` 对象，可以用 [剩余参数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Rest_parameters) 替代。

    > 剩余参数明确表示函数会接收一系列参数，在参数列表中就能看到，不像 `arguments` 那样隐晦；另外，剩余参数是标准数组，而 `arguments` 是类数组对象，要使用数组的方法还要先转为数组。

    ```js
    // 不好
    function joinAll() {
        const args = Array.from(arguments);
        return args.join('');
    }

    // 好
    function joinAll(...args) {
        return args.join('');
    }
    ```

* 使用 [默认参数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Default_parameters) 语法而不是在函数内部处理默认值。

    ```js
    // 不好
    function handleThings(opts) {
        // 如果 opts 传值为 false，这里就会错误的重新指定默认值
        opts = opts || {};

        // ...
    }

    // 不好
    function handleThings(opts) {
        if (typeof opts === 'undefined') {
            opts = {};
        }

        // ...
    }

    // 好
    function handleThings(opts = {}) {
        // ...
    }
    ```

* 将默认参数放置于最后。

    ```js
    // 不好
    function handleThings(opts = {}, name) {
        // ...
    }

    // 好
    function handleThings(name, opts = {}) {
        // ...
    }
    ```

* 不要使用 `Function` 构造函数生成一个函数。

    > 用这种方式生成函数来计算字符串类似于 `eval`，可能造成很多漏洞。

    ```js
    // 不好
    var add = new Function('a', 'b', 'return a + b');
    ```

* 使用 [扩展运算符](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Spread_operator) `...` 给函数传参。

    ```js
    // 不好
    const x = [1, 2, 3, 4, 5];
    console.log.apply(console, x);

    // 好
    const x = [1, 2, 3, 4, 5];
    console.log(...x);
    ```

### 箭头函数

* 当你使用一个函数表达式（或者传递一个匿名函数）时，请使用 [箭头函数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions)。

    ```js
    // 不好
    [1, 2, 3].map(function (x) {
        const y = x + 1;
        return x * y;
    });

    // 好
    [1, 2, 3].map(x => {
        const y = x + 1;
        return x * y;
    });
    ```

* 避免可能让人混淆箭头函数符号 `=>` 和比较运算符 `>=`、`<=` 的代码。

    ```js
    // 不好
    const itemHeight = item => item.height >= 256 ? item.largeSize : item.smallSize;

    // 好
    const itemHeight = item => (item.height >= 256 ? item.largeSize : item.smallSize);

    // 好
    const itemHeight = item => {
        const { height, largeSize, smallSize } = item;
        return height >= 256 ? largeSize : smallSize;
    };
    ```

### 类

* 总是使用 `class`，避免直接操作 `prototype`。

    > 这是因为 `class` 更简洁易懂。

    ```js
    // 不好
    function Queue(contents = []) {
        this.queue = [...contents];
    }
    Queue.prototype.pop = function () {
        const value = this.queue[0];
        this.queue.splice(0, 1);
        return value;
    };

    // 好
    class Queue {
        constructor(contents = []) {
            this.queue = [...contents];
        }
        pop() {
            const value = this.queue[0];
            this.queue.splice(0, 1);
            return value;
        }
    }
    ```

* 使用 `extends` 实现继承。

    ```js
    class Parent {
        constructor(name) {
            this.name = name;
        }
        
        print() {
            console.log(this.name);
        }
    }
    
    // 不好
    function Child(name) {
        this.name = name;
    }

    Child.prototype = Object.create(Parent.prototype);

    // 好
    class Child extends Parent {}
    ```

* 如果类的方法没有显式返回值，建议返回 `this` 。

    > 这样可以帮助构建方法链，实现链式调用。

    ```js
    // 好
    class Div {
        setHeight(height) {
            this.height = height;
        }

        setWidth(width) {
            this.width = width;
        }
    }

    var div = new Div();

    // 返回 undefined
    div.setHeigth(200);  

    // 返回 undefined
    div.setWidth(300);  

    // 最佳
    class Div {
        setHeight(height) {
            this.height = height;
            return this;
        }

        setWidth(width) {
            this.width = width;
            return this;
        }
    }

    var div = new Div();
    div.setHeight(200).setWidth(300);
    ```

* 如果没有给类显式指定构造函数，那它会有一个预设的默认构造函数。一个空的或者仅仅委派给父类的构造函数是不必要的。

    ```js
    // 不好
    class Jedi {
        constructor() {}

        getName() {
            return this.name;
        }
    }

    // 不好
    class Rey extends Jedi {
        constructor(...args) {
            super(...args);
        }
    }

    // 好
    class Rey extends Jedi {
        constructor(...args) {
            super(...args);
            this.name = 'Rey';
        }
    }
    ```

* 避免定义重复的类成员。

    > 类的重复成员会默认最后一个为有效，重复成员多数情况下都是 bug。

    ```js
    // 不好
    class Foo {
        bar() { return 1; }
        bar() { return 2; }
    }

    // 好
    class Foo {
        bar() { return 2; }
    }
    ```

### 属性

* 使用 `.` 号访问属性，仅对无效的属性名才使用方括号。

    ```js
    const person = {
        age: 20,
        'first-name': 'Ada'
    }

    // 不好
    const age = person['age'];

    // 好
    const age = person.age;
    const firstName = person['first-name'];
    ```

* 访问多层级属性时，每层属性都需要判断是否存在。

    ```js
    const data = {
        code: 1,
        data: {
            list: [{
                productId: '001'
            }]
        }
    }

    // 不好 - 当 list 是一个空数组时就会报错
    const productId = data.data.list[0].productId;

    // 不好 - 过多的 try catch 会影响性能
    try {
        const productId = data.data.list[0].productId;
    } catch (e) {
        const productId = '未命名';
        console.error('获取属性 productId 时出错！');
    }

    // 好 - 确保不会出现异常，任意一次的判断结果为 false 则 productId = undefined
    const productId = data && data.data && data.data.list && data.data.list[0] && data.data.list[0].productId;

    // 最佳 - 采用我们获取属性值的公共方法
    const productId = commonUtil.getPathValue(data, 'data.list[0].productId', '未命名');
    ```

### 模块

* 不要在多个地方导入同一路径。

    > 这会让代码难以维护。

    ```js
    // 不好
    import foo from 'foo';
    import { named1, named2 } from 'foo';

    // 好
    import foo, { named1, named2 } from 'foo';

    // 好
    import foo, {
        named1,
        named2,
    } from 'foo';
    ```

* 将所有的 `import` 放置于顶部。

    ```js
    // 不好
    import foo from 'foo';
    foo.init();

    import bar from 'bar';

    // 好
    import foo from 'foo';
    import bar from 'bar';

    foo.init();
    ```

### 迭代器

* 避免使用迭代器，尽量用 JavaScript 的高阶函数来替代类似 `for-in`、`for-of` 这样的循环。

    > 使用 [forEach](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/foreach)、[some](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/some)、[every](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/every)、[filter](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)、[map](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/map)、[reduce](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)、[find](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/find)、[findIndex](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/findindex) 等处理一个数组；使用 [Object.keys](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/keys) 生成对象属性的数组。

    ```js
    const numbers = [1, 2, 3, 4, 5];

    // 不好
    let sum = 0;
    for (let num of numbers) {
        sum += num;
    }

    // 好
    let sum = 0;
    numbers.forEach(num => {
        sum += num;
    });

    // 最佳
    const sum = numbers.reduce((total, num) => total + num, 0);

    // 不好
    const increasedByOne = [];
    for (let i = 0; i < numbers.length; i++) {
        increasedByOne.push(numbers[i] + 1);
    }

    // 好
    const increasedByOne = [];
    numbers.forEach(num => {
        increasedByOne.push(num + 1);
    );

    // 最佳
    const increasedByOne = numbers.map(num => num + 1);
    ```

### 条件语句

* 根据实际情况，恰当选用 `if` 或 `switch` 来构建条件语句。

  一般来说，下面几种情况适合使用 `switch`：

    * 枚举表达式的值。这种枚举是可以期望的、平行逻辑关系的。

    * 表达式的值是固定的，不是动态变化的。

    * 表达式的值是有限的，而不是无限的。

    * 表达式的值一般为整数、字符串等类型的数据。

    而 `if` 结构更适合这些情况：

    * 具有复杂的逻辑关系。

    * 表达式的值具有线性特征，如对连续的区间值进行判断。

    * 表达式的值是动态的。

    * 测试任意类型的数据。

    ```js
    // 好
    let msg;
    if (score < 60) {
        msg = '不及格';
	} else if (score >= 60 && score < 75) {
        msg = '合格';
	} else if (score >= 75 && score < 90) {
        msg = '良好';
	} else {
        msg = '优秀';
	}

    // 好
    let msg;
    switch (sex) {
        case '女':
            msg = '女士';
            break;
        case '男':
            msg = '先生';
            break;
        default:
            msg = '请选择性别';
    }
    ```

* 所有的 `switch` 语句都要包含 `default` 情况，即使 `default` 内容为空。

    > 总是明确说明默认情况是什么，可以提醒开发人员是否忘记了去处理默认情况，让逻辑更严谨。

    ```js
    // 不好
    switch (code) {
        case '1':
            // ...
            break;
    }

    // 好
    switch (code) {
        case '1':
            // ...
            break;
        default:
            // ...
    }

    // 好 - 默认情况就是什么都不做
    switch (code) {
        case '1':
            // ...
            break;
        default:
    }
    ```

### 运算符

* 使用 `===` 和 `!==` 进行比较运算。

    ```js
    // 不好
    if (code == '1') {
        // ...
    }

    // 好
    if (code === '1') {
        // ...
    }
    ```

* 避免不必要的三元运算符。

    ```js
    // 不好
    const foo = a ? a : b;
    const bar = c ? true : false;
    const baz = c ? false : true;

    // 好
    const foo = a || b;
    const bar = !!c;
    const baz = !c;
    ```

### 类型转换

* 转换为字符串。

    > 

    ```js
    const num = 9;

    // 不好
    const score = num + '';
    
    // 不好 - num 不一定有 toString 方法，比如：num 为 null
    const score = num.toString();

    // 好
    const score = String(num);
    ```

* 转换为数字。

    ```js
    const inputValue = '4';

    // 不好
    const val = new Number(inputValue);

    // 不好
    const val = +inputValue;

    // 不好
    const val = inputValue >> 0;

    // 好
    const val = parseInt(inputValue);

    // 好
    const val = Number(inputValue);
    ```

* 转换为布尔值。

    ```js
    const age = 0;

    // 不好
    const hasAge = new Boolean(age);

    // 好
    const hasAge = Boolean(age);

    // 最佳
    const hasAge = !!age;
    ```

* 条件语句如 `if` 会自动进行类型转换，并遵循如下规则：
    * 字符串：空字符串转换为 `false`，否则为 `true`
    * 数字：+0，-0，NaN 转换为 `false`，否则为 `true`
    * 布尔值：返回原布尔值
    * undefined：转换为 `false`
    * null：转换为 `false`
    * 对象：转换为 `true`

    ```js
    const obj = {};
    const arr = [];

    // 不好 - 对象、数组始终为 true
    if (obj) {
        // ...
    }

    if (arr) {
        // ...
    }

    // 好
    if (Object.keys(obj).length) {
        // ...
    }

    if (arr.length) {
        // ...
    }
    ```

### 注释

* 对于类、方法、复杂的代码逻辑、从名称上难以理解的变量、正则表达式等，尽可能加上注释，以便于后期维护。

    ```js
    // 是否是由 tab 切换引起的页面滚动
    let isScrollingByTab = false;

    /**
     * 获取对象的指定属性
     * 属性可以是一个用点号连接的多层级路径
     * @param {object} object 对象
     * @param {string} path 属性值，可以是路径，如：'a.b.c[0].d'
     * @param {any} [defaultVal=''] 取不到属性时的默认值
     * @returns {any} 获取到的属性值
     */
    function getPathValue(object, path, defaultVal = '') {
        // ...
    }
    ```

* 单行注释使用 `//`，总是在需要注释的内容的上方加入注释，并在注释之前保留一个空行，除非该注释是在当前代码块的第一行。

    ```js
    // 不好
    const active = true;  // 当前 tab 状态

    // 好
    // 当前 tab 状态
    const active = true;

    // 不好
    function getType() {
        console.log('获取type...');
        // 设置默认 type 为 'no type'
        const type = this.type || 'no type';

        return type;
    }

    // 好
    function getType() {
        console.log('获取type...');

        // 设置默认 type 为 'no type'
        const type = this.type || 'no type';

        return type;
    }

    // 好
    function getType() {
        // 设置默认 type 为 'no type'
        const type = this.type || 'no type';

        return type;
    }
    ```

* 多行注释使用 `/** ... */`，并尽可能遵循 [jsdoc](http://www.css88.com/doc/jsdoc/) 注释规范。

    > 遵循 jsdoc 规范的注释，能够很方便的自动生成 api 文档；同时，也能提升编码体验，以 Visual Studio Code 为例，当你调用函数时，会浮动提示该函数的描述、参数类型、返回值等信息。

    ```js
    // 不好
    // 获取对象的指定属性
    // 属性可以是一个用点号连接的多层级路径
    function getPathValue(object, path, defaultVal = '') {
        // ...
    }

    // 好
    /**
    * 获取对象的指定属性
    * 属性可以是一个用点号连接的多层级路径
    */
    function getPathValue(object, path, defaultVal = '') {
        // ...
    }

    // 最佳
    /**
     * 获取对象的指定属性
     * 属性可以是一个用点号连接的多层级路径
     * @param {object} object 对象
     * @param {string} path 属性值，可以是路径，如：'a.b.c[0].d'
     * @param {any} [defaultVal=''] 取不到属性时的默认值
     * @returns {any} 获取到的属性值
     */
    function getPathValue(object, path, defaultVal = '') {
        // ...
    }
    ```

* 在注释内容之前加上 `FIXME: ` 可以提醒自己或其他开发人员这是一个需要修改的问题。

    ```js
    class Calculator extends Abacus {
        constructor() {
            super();

            // FIXME: 不应该使用一个全局变量
            total = 0;
        }
    }
    ```

* 在注释内容之前加上 `TODO: ` 可以提醒自己或其他开发人员这里需要一些额外工作。

    > 在 Visual Studio Code 中，可以安装 [TODO Highlight](https://marketplace.visualstudio.com/items?itemName=wayou.vscode-todo-highlight) 扩展，支持高亮显示 `FIXME:`、`TODO:` 等特殊注释，并自动生成列表展示。

    ```js
    class Calculator extends Abacus {
        constructor() {
            super();

            // TODO: total 要写成可以被传入的参数修改
            this.total = 0;
        }
    }
    ```

## HTML

## CSS

## 性能相关

## 业务相关