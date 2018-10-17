# weapp-adapter for pixi.js

## 主要改动

### 输出TouchEvent

官方的`adapter`并没有把`TouchEvent`绑定到`window`，改动也很简单。首先，修改`src/EventIniter/TouchEvent.js`把默认的`TouchEvent`类输出：
```javascript
export default class TouchEvent {
	...
}
```
随后，修改`src/window.js`，将其输出即可：

```javascript
export TouchEvent from './EventIniter/TouchEvent'
```

### `ajax`相关问题

`PIXI.loader`与`ajax`相关的问题，在`src/XMLHttpRequest.js`中增加：
```javascript
addEventListener(ev, cb) {
  this[`on${ev}`] = cb
}
```