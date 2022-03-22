## 题目

[灵活的操作 JavaScript 数组](http://ife.baidu.com/javascript/arrayMethods.html)

## 解法

<!-- tabs:start -->

#### **Task 1**

```js
// 总分数
let scores = ["88", "90", "100", "45", "60", "98", "32", "99", "80"];
function getTotalScore(scores) {
  let result = scores.reduce((sum, score) => sum + Number(score), 0);
  // console.log(result);
  return result;
}
getTotalScore(scores);

// 平均分
function getAverageScore(scores) {
  let sum = getTotalScore(scores);
  const average = Math.trunc(sum / scores.length);
  // console.log(average);
  return average;
}
getAverageScore(scores);

// 挂科
function getFailScores(scores) {
  const result = scores.filter((score) => score <= 60);
  // console.log(result);
  return result;
}
getFailScores(scores);

//加5分
function getAddFiveScores(scores) {
  const result = scores.map((score) => {
    score = Number(score);
    return score + 5 > 100 ? 100 : score + 5;
  });
  // console.log(result);
}
getAddFiveScores(scores);

//奖学金
function getPrize(scores) {
  const prize = scores
    .filter((scores) => scores > 90)
    .reduce((sum, cur, i, arr) => sum * arr.length);
  // console.log(prize);
}
getPrize(scores);
```

#### **Task 2**

利用数组方法实现下面的功能函数

```js
// 实现两个数组拼接,返回一个新数组
function arrJoin(arr1, arr2) {
  return arr1.concat(arr2);
}
//  测试用例
//     let arr1 = ['1', '2', '3'];
//     let arr2 = ['3', '6', '1']
//     console.log(arrJoin(arr1, arr2)); //-> ['1', '2', '3', '3', '6', '1']

//利用reduce()实现两个数组归并
function arrMerge(arr1, arr2) {
  let result = [...arr1, ...arr2].reduce((acc, cur) => {
    if (acc.indexOf(cur) === -1) acc.push(cur);
    return acc;
  }, []);
  return result;
}
// 测试用例
// let arr1 = ['1', '2', '3'];
// let arr2 = ['3', '6', '1']
// console.log(arrMerge(arr1, arr2));//-> ['1', '2', '3', '6']

// 封装数组去重函数,去除数组中重复的元素,
Array.prototype.norepeat = function () {
  return new Set(this);
};

//测试用例
// let arr = ['a', 'ab', 'a'];
// console.log(arr.norepeat()); //-> ['a', 'ab']

// 实现方法检测数组是否包含特定值
function inArray(arr, target) {
  return arr.indexOf(target) === -1 ? false : true;
}

//测试用例
// let arr = ['a', 'ab', 'a'];
// console.log(inArray(arr, 'b')); //-> false
// console.log(inArray(arr, 'a')); //-> true

// 实现多维数组变为一维数组
function matrixElements(arr) {
  return arr.flat();
}

//测试用例
// let rows = [
//   [2, 3, 5],
//   [1, 2, 4],
//   [8, 5, 5],
// ];
// console.log(matrixElements(rows)); //[2,3,5,1,2,4,8,5,5]
```

#### **Task 3**

编码实现数组和对象的相互转换

对象转为数组：

```js
var scoreObject = {
  Tony: {
    Math: 95,
    English: 79,
    Music: 68,
  },
  Simon: {
    Math: 100,
    English: 95,
    Music: 98,
  },
  Annie: {
    Math: 54,
    English: 65,
    Music: 88,
  },
};

//实现对象转换为数组
function objToArr(obj) {
  var arr = [];
  let entry = Object.entries(obj);
  // 用for of loop
  for (let [name, score] of entry) {
    score = Object.values(score);
    arr.push([name, ...score]);
  }
  return arr;

  // 用forEach loop
  // arr = Object.entries(obj)
  // arr = arr.forEach((e, i, arr) => {
  //取出分数
  //   e[0] = Object.keys(obj)[1]
  //取出名字
  //   e[1] = Object.values(e[1])
  // 取消嵌套
  //   e = e.flat();
  //   console.log(e);
  //   return arr;
  // })
}
// console.log(objToArr(scoreObject));
let scoreArr = objToArr(scoreObject);

// 数组转为对象
// 完全看不懂！这里是抄小黄狗的😭
var menuArr = [
  [1, "Area1", -1],
  [2, "Area2", -1],
  [3, "Area1-1", 1],
  [4, "Area1-2", 1],
  [5, "Area2-1", 2],
  [6, "Area2-2", 2],
  [7, "Area1-2-3", 4],
  [8, "Area2-2-1", 6],
];

function arrToObj(arr) {
  let obj = {};
  // 先都变成object
  for (let [order, name, preId] of arr) {
    obj[order] = {
      name: name,
      submenu: {},
      preId: preId,
    };
  }

  // 整理object层次，筛选放到一个新的object里面
  let menu = {};
  for (let order in obj) {
    //把每一项都提取出来比较

    let id = order;
    //提取菜单内容name/submenu
    let content = {
      name: obj[order].name,
      submenu: obj[order].submenu,
    };
    let preId = obj[order].preId;

    // 排除第一层级
    if (preId === -1) {
      menu[id] = content;
    } else {
      // 给下面层级的menu赋值，
      // 从下往上回溯,先给下层菜单赋值 submenu[id]=content
      // 因为第三个数字(preid)是上级菜单的第一个数字(order)所以用obj[preId].附加到上层菜单中
      obj[preId].submenu[id] = content;
    }
  }
  return menu;
}

// 参考：小黄狗 https://github.com/e-han-cyber/baidu-frontend-prictice/blob/main/day09-10/js/task3.js
// 实现数组转换为对象
// function arrToObj(arr) {
//   let obj = {};
//   let map = {}
//   for (let a of arr) {
//     let id = a[0];
//     let sub = a[2];
//     // 使用 pid 记录上一级菜单
//     map[id] = { name: a[1], pid: sub, submenu: {} }
//   }
//   for (let key in map) {
//     let id = key;
//     let item = map[key];
//     let subid = map[key].pid;

//     if (subid === -1) {
//       obj[id] = item
//       delete item.pid
//     } else {
//       //subid 正好对应要存的 id 的对象
//       map[subid].submenu[id] = item;
//       delete item.pid
//     }
//   }
//   return obj
console.log(arrToObj(menuArr));
let menuObject = arrToObj(menuArr);
```

<!-- tabs:end -->

[Github 源码](https://github.com/sevichee/IFE-Practice/tree/main/Day%2009-10/JS%20%E6%95%B0%E7%BB%84)
