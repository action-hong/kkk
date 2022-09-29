[`@layer`](https://developer.mozilla.org/en-US/docs/Web/CSS/@layer)

1. `@layer` 按照声明顺序，越晚声明的优先级更高，如果两个`@layer`中的规则有冲突，优先级高的规则生效（即使按照css的 权重比较比较低），这样方便有些地方需要覆盖规则时，不必写一个更大权重的规则
2. 没有用`@layer`声明的规则（没有级联层），优先级最高
3. 相同layer的css规则可以多次声明，优先级根据第一次声明的位置。例如如下例子：

```html
<div id="app">
  <p>
    hello world
  </p>
  <span> 
    good job
  </span>
</div>
```

```css
p {
  color: yellow;
}

@layer base {
  div#app p {
    color: red;
    font-size: 40px;
  }

}

@layer utilities {
  div p {
    color: skyblue;
  }

  span {
    color: skyblue;
  }
}

@layer base {

  div#app span {
    color: red;
  }
}
```

utilities的规则优先级高于base，因为base首次声明在最前面，因此模板中的`p`标签显示`yellow`(第1，2点), `span`的颜色为`skyblue`(第3点)