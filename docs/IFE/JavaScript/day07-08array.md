## 题目

[JavaScript 数组基础](http://ife.baidu.com/javascript/arrayBasic.html)

## score.js

```js
/**
 * @description 返回成绩表格 html 字符串
 * @param {array[][]} rows
 * @returns {string} html
 * 返回的字符串格式如下
 *  <tr>
        <td>学生姓名</td>
        <td>学生总分</td>
    </tr>
 */

function renderScoreTableRows(rows) {
  let table = "";
  rows.forEach((student) => {
    let [name, score] = student;
    table += `
    <tr>
        <td>${name}</td>
        <td>${score}</td>
    </tr>`;
  });
  return table;
}

/**
 * @description 返回第一名列表 html 字符串
 * @param {array[][]} rows
 * @returns {string} html
 * 返回的字符串格式如下
 * <li>第一名：学生姓名，分数：学生分数</li>
 */

function printFirst(rows) {
  const [[nameFirst, scoreFirst]] = rows;
  return `<li>第一名：${nameFirst}，分数：${scoreFirst}</li>`;
}

/**
 * @description 返回最后一名列表 html 字符串
 * @param {array[][]} rows
 * * @returns {string} html
 * 返回的字符串格式如下
 * <li>最后一名：学生姓名，分数：学生分数</li>
 */

function printLast(rows) {
  const rowRe = rows.reverse();
  const [[nameLast, scoreLast]] = rowRe;
  return `<li>最后一名：${nameLast}，分数：${scoreLast}</li>`;
}

/**
 * @description 返回平均分 html 字符串
 * @param {array[][]} rows
 * * @returns {string} html
 * 返回的字符串格式如下
 * <li>平均分:平均分分数</li>
 */

function printAverage(rows) {
  let sum = 0;
  rows.forEach((student) => {
    let [, score] = student;
    sum += Number(score);
  });
  average = (sum / rows.length).toFixed(2);
  return `<li>平均分:${average}</li>`;
}
```

[Github 源码](https://github.com/sevichee/IFE-Practice/tree/main/Day%2007-08/JS%20%E6%95%B0%E7%BB%84%E7%BB%83%E4%B9%A0%E4%BB%BB%E5%8A%A1)
