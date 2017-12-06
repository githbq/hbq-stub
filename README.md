> stub: 存根,对对象属性赋值时,进行一个存根方便恢复之前的值

![my love](./logo.png)
## Install
```shell
yarn add light-stub
```

## Code
```javascript
module.exports = Stubs

function Stubs() { }

Stubs.prototype = Object.create(Array.prototype)

Stubs.prototype.stub = function (obj, prop, value) {
  this.push([obj, prop, obj[prop]])
  obj[prop] = value
}

Stubs.prototype.restore = function () {
  let stub
  while (stub = this.pop()) stub[0][stub[1]] = stub[2]
}

```

