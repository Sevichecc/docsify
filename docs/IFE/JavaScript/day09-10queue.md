## 题目

[队列和栈](http://ife.baidu.com/javascript/arrayQueue.html)

## 解法

<!-- tabs:start -->

#### **Tas01 队列 1**

```html
<input id="queue-input" type="text" />
<p id="queue-cont">队列内容：apple-&gt;pear</p>
<button id="in-btn">入队</button>
<button id="out-btn">出队</button>
<button id="front-btn">打印队头元素内容</button>
<button id="empty-btn">判断队列是否为空</button>

<script>
  const btnIn = document.querySelector("#in-btn");
  const btnOut = document.querySelector("#out-btn");
  const btnFront = document.querySelector("#front-btn");
  const btnEmpty = document.querySelector("#empty-btn");
  const queueCont = document.querySelector("#queue-cont");
  const inputQue = document.querySelector("#queue-input");

  var queue = ["apple", "pear"];

  // 入队
  btnIn.addEventListener("click", () => {
    queue.unshift(inputQue.value);
    queueCont.innerHTML = `队列内容：${queue.join("-&gt;")}`;
  });

  // 出队
  btnOut.addEventListener("click", () => {
    queue.pop(queue.at(-1));
    queueCont.innerHTML = `队列内容：${queue.join("-&gt;")}`;
  });

  // 打印队头元素
  btnFront.addEventListener("click", () => {
    queueCont.innerHTML = `队头：${queue.at(-1)}`;
  });

  //判空
  btnEmpty.addEventListener("click", () => {
    queueCont.innerHTML = queue.length === 0 ? "队列为空" : "队列不为空";
  });
</script>
```

#### **Task02 队列 2**

```html
<input id="queue-input" type="text" />
<p id="queue-cont">队列内容：apple &lt;-pear</p>
<button id="in-btn">入队</button>
<button id="out-btn">出队</button>
<button id="front-btn">打印队头元素内容</button>
<button id="empty-btn">判断队列是否为空</button>

<script>
  const btnIn = document.querySelector("#in-btn");
  const btnOut = document.querySelector("#out-btn");
  const btnFront = document.querySelector("#front-btn");
  const btnEmpty = document.querySelector("#empty-btn");
  const queueCont = document.querySelector("#queue-cont");
  const inputQue = document.querySelector("#queue-input");

  var queue = ["apple", "pear"];

  // 入队
  btnIn.addEventListener("click", () => {
    queue.push(inputQue.value);
    queueCont.innerHTML = `队列内容：${queue.join("&lt;-")}`;
  });

  // 出队
  btnOut.addEventListener("click", () => {
    queue.shift(queue.at(0));
    queueCont.innerHTML = `队列内容：${queue.join("&lt;-")}`;
  });

  // 打印队头元素
  btnFront.addEventListener("click", () => {
    queueCont.innerHTML = `队头：${queue.at(0)}`;
  });

  //判空
  btnEmpty.addEventListener("click", () => {
    queueCont.innerHTML = queue.length === 0 ? "队列为空" : "队列不为空";
  });
</script>
```

#### **Task03 栈 1**

```html
<input id="stack-input" type="text" />
<p id="stack-cont">栈内容：apple-&gt;pear</p>
<button id="push-btn">进栈</button>
<button id="pop-btn">退栈</button>
<button id="front-btn">打印栈顶元素内容</button>
<button id="empty-btn">判断栈是否为空</button>

<script>
  const btnPush = document.querySelector("#push-btn");
  const btnPop = document.querySelector("#pop-btn");
  const btnFront = document.querySelector("#front-btn");
  const btnEmpty = document.querySelector("#empty-btn");
  const stackCont = document.querySelector("#stack-cont");
  const input = document.querySelector("#stack-input");
  var stack = ["apple", "pear"];
  // 入栈
  btnPush.addEventListener("click", () => {
    stack.push(input.value);
    stackCont.innerHTML = `队列内容：${stack.join("-&gt;")}`;
  });

  // 出栈
  btnPop.addEventListener("click", () => {
    stack.pop(stack.at(-1));
    stackCont.innerHTML = `队列内容：${stack.join("-&gt;")}`;
  });

  // 打印栈顶元素
  btnFront.addEventListener("click", () => {
    stackCont.innerHTML = `栈顶：${stack.at(-1)}`;
  });

  //判空
  btnEmpty.addEventListener("click", () => {
    stackCont.innerHTML = stack.length === 0 ? "栈为空" : "栈不为空";
  });
</script>
```

#### **Task04 栈 2**

```html
<input id="stack-input" type="text" />
<p id="stack-cont">栈内容：apple&lt-pear</p>
<button id="push-btn">进栈</button>
<button id="pop-btn">退栈</button>
<button id="front-btn">打印栈顶元素内容</button>
<button id="empty-btn">判断栈是否为空</button>

<script>
  const btnPush = document.querySelector("#push-btn");
  const btnPop = document.querySelector("#pop-btn");
  const btnFront = document.querySelector("#front-btn");
  const btnEmpty = document.querySelector("#empty-btn");
  const stackCont = document.querySelector("#stack-cont");
  const input = document.querySelector("#stack-input");
  var stack = ["apple", "pear"];
  // 入栈
  btnPush.addEventListener("click", () => {
    stack.unshift(input.value);
    stackCont.innerHTML = `队列内容：${stack.join("&lt-")}`;
  });

  // 出栈
  btnPop.addEventListener("click", () => {
    stack.shift(stack.at(0));
    stackCont.innerHTML = `队列内容：${stack.join("&lt-")}`;
  });

  // 打印栈顶元素
  btnFront.addEventListener("click", () => {
    stackCont.innerHTML = `栈顶：${stack.at(0)}`;
  });

  //判空
  btnEmpty.addEventListener("click", () => {
    stackCont.innerHTML = stack.length === 0 ? "栈为空" : "栈不为空";
  });
</script>
```

<!-- tabs:end -->

[Github 源码](https://github.com/sevichee/IFE-Practice/tree/main/Day%2009-10/JS%20%E9%98%9F%E5%88%97%E5%92%8C%E6%A0%88)
