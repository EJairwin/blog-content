# blog-content

收集日常工具类



```js
/*Array删除*/
Array.prototype.newSplice = function(id){
    for ( let i = 0 ; i < this.length ;i++ ) this[i].id ? ( id === this[i].id && this.splice(i,1) ) : ( id === this[i] && this.splice(i,1) );
    return this;
};

//删首尾空
const trim = string => string.replace(/(^\s*)|(\s*$)/g, "");

//金额指定格式 只允许2位小数 9位整数
const price = string => {
    let value = string;
    //清除"数字"和"."以外的字符
    value = value.replace(/[^\d.]/g, "");
    //验证第一个字符是数字而不是
    value = value.replace(/^\./g, "");
    //只保留第一个. 清除多余的
    value = value.replace(/\.{2,}/g, ".");
    value = value.replace(".", "$#$").replace(/\./g, "").replace("$#$", ".");
    //只能输入两个小数
    value = value.replace(/^(-)*(\d+)\.(\d\d).*$/, '$1$2.$3');
    if ( value !== '' ) {
        let value2 = value.split('.');
        if ( value2[0].length > 9 ) {
            value = value2[0].substr(0, 9) + (value2[1] ? '.' + value2[1] : '');
        }
    }
    return value;
};

//整数
const integer = string => {
    let value =  string.match(/^-?[0-9]\d*/) || string.match(/-?/);
    return value ? value[0] : '';
};

const timeString = timestamp => {
    return moment(timestamp * 1000).format('YYYY-MM-DD HH:mm');
};

/*4种随机颜色的封装*/
function colorConversion(){
    let color = Math.ceil(Math.random()*16777215).toString(16);
    while (color.length < 6){
        color += "0" + color;
    }
    return `#${color}`;
}
/*数组颜色*/
function arrayColor(){
    return "#" + (color => {
        return new Array(7-color.length).join("0") + color
    })((Math.random() * 0x1000000 << 0).toString(16))
}
function randomColor(){
    const r = Math.floor(Math.random()*256),
        g = Math.floor(Math.random()*256),
        b = Math.floor(Math.random()*256);
    return `rgb(${r},${g},${b})`;/*IE7不支持rgb;*/
}
function randomRange(min,max){
    return Math.floor((max-min+1)*Math.random()+min);
}
/*randomColour()引用了randomRange()*/
function randomColour(){
    const r = randomRange(0,255),
        g = randomRange(0,255),
        b = randomRange(0,255);
    return `rgb(${r},${g},${b})`;
}
/*根据id获取dom对象*/
function byId(id){
	return document.getElementById(id);
}
```

```js
export function isEmail (email) {
  return /^([A-Za-z0-9_\-.])+@(qq.com|foxmail.com|vip.qq.com)$/.test(email)
}

export function codePassword (code) {
  return /^(?=.*\d)(?=.*[a-z]).{8,10}$/.test(code)
}

export function passwordStrength (code) {
  return /^(?![0-9]+$)(?![a-z]+$)[0-9a-z]{6,10}$/.test(code)
}

export function isChinese (word) {
  return /[^\u4E00-\u9FA5]/g.test(word)
}

export function isNumber (num) {
  return /^[0-9]*$/.test(num)
}

export function isWx (wx) {
  return /^[a-zA-Z]([-_a-zA-Z0-9]{5,19})+$/.test(wx)
}

export function isEnglish (eng) {
  return /[^a-zA-Z]/g.test(eng)
}

export function isPhone (number) {
  return /^1[0|1|2|3|4|5|6|7|8|9]\d{9}$/.test(number)
}

export function isQq (qq) {
  return /^[1-9]\d{4,12}$/.test(qq)
}
```

