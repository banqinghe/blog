## yocto-queue 和 p-limit

TAG: JavaScript
DATE: 2022/05/24

原生 JavaScript 的 `Array.prototype.shift()` 时间复杂度是 O(N) 的，如果有一个较大的队列需要经常做 `shift` 操作，使用 `yocto-queue` 是个更好的选择。

这是 `p-limit` 的依赖库，`p-limit` 是做 `Promise.all` 限流的库。在有关限流的 StackOverflow 问题里，一个使用 `await` + `splice` 的方法也能达到限流效果，很巧妙。

[What is the best way to limit concurrency when using ES6's Promise.all()?](https://stackoverflow.com/questions/40639432/what-is-the-best-way-to-limit-concurrency-when-using-es6s-promise-all)

---

## !important

TAG: CSS

`!important` 优先级大于内联样式。

google translate 插件的浮窗 `z-index` 值是 1201，有时候会被更大的 `z-index` 覆盖。

---

## CSS counter

TAG: CSS
DATE: 2022/05/21

CSS `counter()` 函数

```css

```

---

## :focus-within

TAG: CSS
DATE: 2022/05/19

`:focus-within` 伪类：当该元素或该元素的子元素获取焦点的时候生效（即该元素或子元素触发 `:focus`）。在 daisyui 组件库中实现 dropdown 组件时使用到，用于切换 dropdown content 是否展示。

```css
.dropdown.dropdown-open .dropdown-content,
.dropdown.dropdown-hover:hover .dropdown-content,
.dropdown:not(.dropdown-hover):focus .dropdown-content,
.dropdown:not(.dropdown-hover):focus-within .dropdown-content {
  @apply visible opacity-100;
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
