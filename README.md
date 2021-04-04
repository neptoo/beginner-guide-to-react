# Beginner Guide To React -React入门指南

创建时间：2021/03/29

> [Beginner Guide To React](https://egghead.io/courses/the-beginner-s-guide-to-react) 教程作者：[Kent C. Dodds](https://github.com/kentcdodds)



## React.createElement

`React.createElement` 类似于原生JS中的 `document.createElement` ，后者创建的是 `DOM`节点，前者创建的是 `React DOM` 节点。API:

```javascript
React.createElement(
   type,
   [props],
   [...children]
)
```

示例：

```html
<script src="https://unpkg.com/react@16.7.0/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@16.7.0/umd/react-dom.production.min.js"></script>
  <script type="text/javascript">
    const rootElement = document.getElementById('root')
    /* 不同于原生JS中获取元素然后将属性赋给元素 此处是将属性以对象的形式创建 */
    const element = React.createElement('div', {
      children: 'Hello World',
      className: 'container'
    })
    // ReactDOM
    ReactDOM.render(element, rootElement)
</script>
```

上面例子中 children 是直接在 props 中声明的，它也可以作为第三方参数传入。

```javascript
const rootEl = document.querySelector('#root');
const childEl = React.createElement('span', {}, 'hey there');
const el = React.createElement('div', {
   className: 'container',
}, childEl);
ReactDOM.render(el, rootEl);
```

React 也可以作为 React 子元素（有点绕，看例子👇）

```javascript
const rootElement = document.getElementById('root')
const element = React.createElement('div', {
      // create additional React Dom Element as children
   children: React.createElement('span', null, 'Hi World'),
   className: 'container'
})
ReactDOM.render(element, rootElement)
```



## JSX

> 使用 Babel 将 JSX 转换为 JavaScript [Babel在线转换](https://babeljs.io/repl)

JSX 让我们可以以类似HTML的方式创建元素

```html
<script type="text/babel">
  const rootElement = document.getElementById('root');
  const element = (
    <div className="container">
      <h1>Hello World</h1>
    </div>
  );
  ReactDOM.render(element, rootElement);
</script>
```

> 需要注意的是上面使用的是 `className` 而不是 `class`

在 JSX 中使用 javascript, 需要用到 `{}`

```jsx
const rootElement = document.getElementById('root')
const myClassName = 'container'
const children = 'Hello World'
const element = <div className={myClassName}>{children}</div>
ReactDOM.render(element, rootElement)
```

可以在一个对象中定义所有的属性

```jsx
const rootElement = document.getElementById('root')
const className = 'container'
const children = 'Hello World'
const props = {className, children}
const element = <div {...props} />
ReactDOM.render(element, rootElement)
```

并且你可以在后面rewrite该属性

```jsx
const element = <div id="app-root" {...props} className="not-container" />
```

