---
id: toastandroid
title: ToastAndroid
---

本模块将原生的 ToastAndroid 模块导出为一个 JS 模块，用于在 Android 设备上显示一个悬浮的提示信息。本模块包含一个`show`方法接受以下的参数：

1.  String message: 一个字符串，表示将要显示的文本内容。
2.  int duration: 提示信息持续显示的时间。可以是`ToastAndroid.SHORT`或者`ToastAndroid.LONG`。

还有一个名为`showWithGravity`的方法可以指定弹出的位置。可选项有：ToastAndroid.TOP, ToastAndroid.BOTTOM, ToastAndroid.CENTER.

The 'showWithGravityAndOffset' function adds on the ability to specify offset These offset values will translate to pixels.

用法示例：

```jsx
import { ToastAndroid } from 'react-native'; 

ToastAndroid.show("A pikachu appeared nearby !", ToastAndroid.SHORT);
ToastAndroid.showWithGravity(
  "All Your Base Are Belong To Us",
  ToastAndroid.SHORT,
  ToastAndroid.CENTER
);
ToastAndroid.showWithGravityAndOffset(
  "A wild toast appeared!",
  ToastAndroid.LONG,
  ToastAndroid.BOTTOM,
  25,
  50
);
```

### 进阶用法:

The ToastAndroid API is imperative and this might present itself as an issue, but there is actually a way(hack) to expose a declarative component from it. See an example below:

```jsx
import React, { Component } from 'react';
import {
  View,
  Button,
  ToastAndroid,
} from 'react-native';

// a component that calls the imperative ToastAndroid API
const Toast = (props) => {
  if (props.visible) {
    ToastAndroid.showWithGravityAndOffset(
      props.message,
      ToastAndroid.LONG,
      ToastAndroid.BOTTOM,
      25,
      50
    );
    return null;
  }
  return null;
};

class App extends Component {
  constructor(props) {
    super(props);
    this.state = {
      visible: false,
    };
  }
   handleButtonPress = () => {
    this.setState({
        visible: true,
    }, () => {
      this.hideToast();
    });
  };
   hideToast = () => {
    this.setState({
      visible: false
    })
  }
   render() {
    return (
      <View style={styles.container}>
        <Toast
          visible={this.state.visible}
          message="Example"
        />
        <Button title="Toggle Modal" onPress={this.handleButtonPress} />
      </View>
    );
  }
}
```

### 查看方法

- [`show`](toastandroid.md#show)
- [`showWithGravity`](toastandroid.md#showwithgravity)
- [`showWithGravityAndOffset`](toastandroid.md#showwithgravityandoffset)

### 查看属性

- [`SHORT`](toastandroid.md#short)
- [`LONG`](toastandroid.md#long)
- [`TOP`](toastandroid.md#top)
- [`BOTTOM`](toastandroid.md#bottom)
- [`CENTER`](toastandroid.md#center)

---

# 文档

## 方法

### `show()`

```jsx
static show(message, duration)
```

---

### `showWithGravity()`

```jsx
static showWithGravity(message, duration, gravity)
```

---

### `showWithGravityAndOffset()`

```jsx
static showWithGravityAndOffset(message, duration, gravity, xOffset, yOffset)
```

## 属性

### `SHORT`

Indicates the duration on the screen.

```jsx
ToastAndroid.SHORT;
```

---

### `LONG`

Indicates the duration on the screen.

```jsx
ToastAndroid.LONG;
```

---

### `TOP`

Indicates the position on the screen.

```jsx
ToastAndroid.TOP;
```

---

### `BOTTOM`

Indicates the position on the screen.

```jsx
ToastAndroid.BOTTOM;
```

---

### `CENTER`

Indicates the position on the screen.

```jsx
ToastAndroid.CENTER;
```
