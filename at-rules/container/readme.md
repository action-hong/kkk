## @container, 容器查询

```
container: container-type container-name
```

当然也可以分开声明:

```css
container-type: inline-size
container-type: size
container-type: normal
```

其实normal是默认值，即`@container`不会起作用。

## inline-size

可以让`@container`起作用，让该元素变成一个可以查询其宽度的容器（一维）：

如下：

```css
@container (max-width: 300px) {
  p {
    background: yellow;
  }
}

div {
  container-type: inline-size 
}
```

```html
<div>
  <p>hello</p>
</div>
```

则在div的宽度小于`300`时，其内部的`p`元素的背景颜色为`yellow`

如果想查询其高度变化:

```css
@container (max-height: 300px) {
  p {
    color: red;
  }
}
```

此时再`div`高度小于`300px`的时候并不会起作用，因为此时是`inline-size`。只需设置成`size`就能起作用了

```css
container-type: size;
```

---

## container-name

如上的`@container`会对所有满足调节的容器成立，而有时我们只想让某些元素成立，此时可以使用`container-name`

```diff
- @container (max-width: 300px) {
+ @container aside (max-width: 300px) {
  p {
    background: yellow;
  }
}

div {
  container-type: inline-size; 
+ container-name: asize;
}

```

在`container`后面加上限定的`container-name`即可