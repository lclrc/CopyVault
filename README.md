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

### 中文排版(在中英字符、数字、标点和货币符号之间添加空格)
> From 阿立

```js
function main(text) {
    // 使用正则表达式匹配并在中英字符、数字、标点和货币符号之间添加空格
    return text.replace(/([\u4e00-\u9fa5])([a-zA-Z0-9¥$€£₹₩₽₺₨₦₫₴₭₲₡₣₤₱])/g, '$1 $2')
      .replace(/([a-zA-Z0-9¥$€£₹₩₽₺₨₦₫₴₭₲₡₣₤₱])([\u4e00-\u9fa5])/g, '$1 $2')
      .replace(/([\u4e00-\u9fa5])([,.!?;:¥$€£₹₩₽₺₨₦₫₴₭₲₡₣₤₱])/g, '$1$2')
      .replace(/([,.!?;:¥$€£₹₩₽₺₨₦₫₴₭₲₡₣₤₱])([\u4e00-\u9fa5])/g, '$1 $2');
}
```

### 复制抖音评论去除用户名
> From 阿立

```js
function main(text) {
    // 使用正则表达式匹配并删除 ^@.*: 部分
    const regex = /^@.*?:/gm;
    const cleanedText = text.replace(regex, '').trim();

    return cleanedText;
}
```

### 哔哩哔哩RSS 复制UID
> From 阿立

```js
function main(text) {
    const regex = /UID:(\d+)/g;
    let match;
    const results = [];
    const prefix = "https://rsshub.app/bilibili/user/dynamic/";

    while ((match = regex.exec(text)) !== null) {
        results.push(prefix + match[1]);
    }

    return results.length === 1 ? results[0] : results;
}
```

### 精简App Store分享链接
> From 阿立

```js
function main(url) {
    // 使用正则表达式提取国家代码和ID部分
    const regex = /https:\/\/apps\.apple\.com\/([a-z]{2})\/app\/.*\/id(\d+)/;
    const match = url.match(regex);

    if (match) {
        // 构建精简后的链接
        const countryCode = match[1];
        const appId = match[2];
        const simplifiedUrl = `https://apps.apple.com/${countryCode}/app/id${appId}`;
        return simplifiedUrl;
    } else {
        return "Invalid URL";
    }
}
```

### 删除多余的空行段落
> From 阿立

```js
function removeEmptyLines(text) {
    return text.split('\n').filter(line => line.trim() !== '').join('\n');
}

function main(text) {
    return removeEmptyLines(text);
}
```
