# Node.js应用开发入门

## 入口程序

一般而言，我们使用`app.js`作为入口程序的名字：

```js
'use strict';
module.exports = require('@rokid/vui')({
  created() {
    // 在应用第一次被唤起时调起
  },
  resumed() {
    // 在应用被置为栈顶恢复时调起
  },
  paused() {
    // 在应用被其他应用占用时调起
  },
  onrequest(context) {
    // 在接收到语音请求后调起
  },
  beforeDestroy() {
    // 在应用被停止时调起
  },
  destroyed() {
    // 在应用被销毁时调起
  }
});
```

另外，可以在生命周期函数内使用如下方法：

- `.say(text)` 语音合成(TTS)；
- `.pickup()` 打开拾音并接受语音指令；
- `.exit()` 退出当前应用，并且关闭拾音；

更复杂的例子可以参考 `/opt/apps/` 目录下的内置应用。

## 其他系统接口

为了让开发者完成各种开放性的技能需求，RokidOS 为本地技能开发者提供了如下系统基础接口：

### 语音合成

样例：

```js
const tts = require('@rokid/tts');
tts.say('text to speech');
```

该模块提供以下方法：

- `play(text, callback)` 让若琪说出指定的文字内容
  - {String} `text` 需要让若琪说的文字，支持 `SSML`
  - {Function} `callback` 当 `tts` 完成、取消或其他方式结束时，会通过这个回调函数通知用户
- `stop()` 停止播放当前内容

### 多媒体播放

样例：

```js
const player = require('@rokid/player');
player.play(url);
player.stop();
player.resume();
player.pause();
```

该模块提供以下方法：

- `play(url)` 播放某个 `url` 的媒体
  - {String} `url` 媒体地址
- `stop()` 停止当前应用中所有的媒体播放
- `pause()` 暂停当前应用中所有的媒体播放
- `resume()` 恢复当前应用中所有的媒体播放

### 灯光控制

样例：

```js
const light = require('@rokid/lumen');
light.fill('red', 'all');
light.update({
  [1]: 'red',
  [2]: 'green',
});
```

该模块提供以下方法：

- `fill(color, sets)` 向指定的 LED 填充单个颜色
  - {String} `color` `RGB` 颜色值，支持的格式：#000000、red
  - {Array} `sets` 表示需要填充颜色的 LED 坐标，目前 LED 阵列为一维
- `update(dataWithSets)` 更底层的填充方法，一般用于更复杂的灯光渲染需求
  - {Object} `dataWithSets` 该对象是 `LED-Color` 的映射关系
- `gradients(dataWithSets, ms)` 提供灯光的渐变控制

