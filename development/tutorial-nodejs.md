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

- `say(text, callback)` 让若琪说出指定的文字内容
  - {String} `text` 需要让若琪说的文字，支持 `SSML`
  - {Function} `callback` 当 `tts` 完成、取消或其他方式结束时，会通过这个回调函数通知用户
- `stop()` 停止播放当前内容

### 多媒体播放

样例：

```js
const player = require('@rokid/player');
player.play(url);
player.stop();
player.pause();
player.resume();
```

该模块提供以下方法：

- `play(url)` 播放某个 `url` 的媒体；
  - {String} `url` 媒体地址；
- `stop()` 停止当前应用中所有的媒体播放；
- `pause()` 暂停当前应用中所有的媒体播放；
- `resume()` 恢复当前应用中所有的媒体播放；

### 灯光控制

- `startRound(color)` 转圈开始；
- `stopRound()` 停止转圈；
- `startBlink(color)` 眨眼效果；
- `stopBlink()` 停止眨眼效果；
- `createLayer(leds, options)` 通过指定的 LED 数目创建图层；
- `removeAllLayers()` 移除当前所有图层；

图层(`LumenLayer`)接口：

- 该对象通过 `createLayer()` 返回；
- `fill(color)` 填充某个颜色；
- `fade(from, to, speed)` 颜色渐变；

### 蓝牙控制

- `open()` 打开蓝牙；
- `close()` 关闭蓝牙；

A2DP 模式

- `a2dp(type)` 开启 `a2dp` 模式，`type` 为：`sink` 与 `link`；
- `play()` 播放已连接设备的音乐；
- `stop()` 停止已连接设备的音乐；
- `pause()` 暂停蓝牙音乐；

BLE 模式

- `ble()` 打开并返回 `BluetoothLowEnergy` 对象；
- `.onResp(cb)` 从 BLE 通道中获取数据；


## 插件

Node.js 提供了插件机制用于让开发者可以定制一些系统级的特性。

### 系统事件捕获

Node.js 提供了可以通过脚本的方式直接捕获一些系统事件，现支持：

- [x] `voice info`    语音信息，会附带能量值
- [x] `voice wakeup`  语音唤醒
- [x] `voice error`   语音错误
- [x] `speech`        实时语音识别事件，会返回识别结果和状态
- [x] `tts start`     tts 开始说话
- [x] `tts end`       tts 结束
- [x] `pickup start`  开始拾音
- [x] `pickup end`    结束拾音

首先创建如下文件 `/data/plugins/EventHandler.js`，然后该文件内写入如下代码：

```js
const EventEmitter = require('events').EventEmitter;
const handler = module.exports = new EventEmitter();
handler.on('voice info', (data) => {
  // data.energy 当前语音的能量值
});
handler.on('voice wakeup', (data) => {
  // 语音唤醒事件
});
handler.on('voice error', (err) => {
  // TODO
})
handler.on('speech', (data) => {
  // 通过`data.text`获取文本
  // 通过`data.state`获取识别状态：complete, pending
});
handler.on('tts start', (text) => {
  // TTS开始事件，并返回TTS的语句
});
handler.on('tts end', () => {
  // TTS结束事件
});
handler.on('pickup start', (data) => {
  // 拾音开始
});
handler.on('pickup end', (data) => {
  // 拾音结束
});
```

这里注意，一定要把该对象设置到 `module.exports` 返回，否则将无法生效。
