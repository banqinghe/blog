## queueMicrotask

TAG: JavaScript
DATE: 2022/05/09

`queueMicrotask(fn)` 方法可以创建一个微任务，比 `Promise.resolve()` 更好用。

[在 JavaScript 中通过 queueMicrotask() 使用微任务](https://developer.mozilla.org/zh-CN/docs/Web/API/HTML_DOM_API/Microtask_guide)

---

## <details> 和 <summary>

TAG: HTML
DATE: 2022/05/09

在 MDN 侧边栏发现的。这两个元素配合可实现原生的 展开  ⇄ 闭合 效果。

```html
<details>
  <summary>Details</summary>
  Something small enough to escape casual notice.
</details>
```

---

## Web Code Editor

complex：Monaco，CodeMirror，Ace

simple: react-simple-code-editor（只有简单的高亮功能）

---

## 深拷贝

TAG: JavaScript
DATE: 2022/05/14

[structuredClone](https://developer.mozilla.org/zh-CN/docs/web/api/structuredClone) 提供深拷贝功能。利用结构化克隆算法。支持循环引用，但是不支持函数属性。core-js 提供了 polyfill。

一个之前学的一个深拷贝实现：

```javascript
function deepClone(target, map = new Map()) {
  if (typeof target === 'object' && target !== null) {
    const cache = map.get(target);
    if (cache) {
      return cache;
    }

    const result = Array.isArray(target) ? [] : {};
    map.set(target, result);
    
    if (Array.isArray(target)) {
      target.forEach((item, index) => {
        result[index] = deepClone(item, map);
      })
    } else {
      for (let )
      Object.keys(target).forEach((key) => {
        result[key] = deepClone(target[key], map);
      });
    }

    return result;
  } else {
      return target;
  }
}
```

---

## JSX 中的多条件渲染

TAG: JSX
DATE: 2022/05/15

从 TypeScript 官网看到的写法，利用对象在 JSX 中模拟 switch 语句

```jsx
<div>
  {{
    0: (
      <ShowErrorsExample />
    ),
    1: (
      <TypeDefinitionsExample />
    ),
    2: (
      <InterfaceExample />
    ),
    3: (
    <ReactExample />
    ),
  }[index]}
</div>
```
