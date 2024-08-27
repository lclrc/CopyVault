中文 | [English](https://github.com/lclrc/CopyVault/blob/main/README_EN.md)

# CopyVault

## 脚本(JavaScript)
**要求：**
- 脚本内至少应包含一个main函数，可接收一个参数。执行时，将把文本内容作为参数传递给main函数
- main函数返回值：可以是字符串或字符串数组。当返回字符串数组时，将把数组中所有字符串显示成多个选项以供选择

**欢迎PR**

### 反转文字

比如：原始文本为`Hello World`，将输出`dlroW olleH`

```js
function main(str) {
    return str.split('').reverse().join('');
}
```

### 按换行分割

比如：原始文本为：
```
Hello
World
```
将弹出选择框，框内文本分别为`Hello`和`World`

可用于多条相关联信息保存在一条记录内，分割符可自选

```js
function main(str) {
    arr = str.split("\n");
    arr.forEach((item, index)=>{
      if(!item){
          arr.splice(index, 1);
      }
    })
    return arr;
}
```

### 转为MD项目列表
比如：原始文本为`Hello World`，将输出`- Hello World`

```js
function main(str) {
    const bullet = '-';
    return `${bullet} ` + str.split(/\r?\n/).join(`\n${bullet} `);
}
```

### GitHub转换raw链接
比如：原始文本为`https://raw.githubusercontent.com/lclrc/CopyVault/main/README_EN.md`，将输出`https://github.com/blob/lclrc/CopyVault/main/README_EN.md`

```js
function main(url) {
  // 处理字符串，将 "raw.githubusercontent.com" 替换为 "github.com/blob"
  const processedUrl = url.replace("raw.githubusercontent.com", "github.com/blob");
  // 创建一个字符串数组
  const urls = [];
  // 将处理后的字符串添加到数组中
  urls.push(processedUrl);
  // 返回字符串数组
  return urls;
}
```

### 转换为大写
比如：原始文本为`Hello World`，将输出`HELLO WORLD`

```js
function main(str) {
  // 创建一个字符串数组
  const strs = [];
  // 处理字符串，转换为大写
  const processedStr = str.toUpperCase();
  // 将处理后的字符串添加到数组中
  strs.push(processedStr);
  // 返回字符串数组
  return strs;
}
```
### 去掉全部空格
比如：原始文本为`Hello World`，将输出`HelloWorld`

```js
function main(str) {
  // 创建一个字符串数组
  const strs = [];
  // 处理字符串，去除所有空格
  const processedStr = str.replace(/\s/g, "");
  // 将处理后的字符串添加到数组中
  strs.push(processedStr);
  // 返回字符串数组
  return strs;
}
```

### 去掉首尾空格
比如：原始文本为`  Hello World `，将输出`Hello World`

```js
function main(str) {
  // 创建一个字符串数组
  const strs = [];
  // 处理字符串，去除首尾空格
  const processedStr = str.trim();
  // 将处理后的字符串添加到数组中
  strs.push(processedStr);
  // 返回字符串数组
  return strs;
}
```
