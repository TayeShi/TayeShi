# <Img>

在HTML中嵌入一个图片。

一般用法：

```html
<img class="xxx" src="imageUrl" alt="xxxxxx" />
```



## 属性

- alt - 备用文本描述
- height - 图像的高度
- width - 图像的宽度
- crossorigin - todo
- decoding - todo
- ismap - todo
- size - todo
- srcset - todo
- usemap - todo
- loading - no
- importance - no
- referrerpolicy - no

> todo的为后期可写可不写的，有用到了再补
>
> no的为没必要记的
>
> 如果有样式，一般通过css进行添加

## 实用技巧

### 固定宽高中显示图片

经常出现固定宽高中显示一张图片，比如Logo区域的显示，图片空间图片列表显示。

对图片可显示区域宽高是固定的，适配图片自显示。

处理方式：外部div设置固定宽高，内部img宽高都为100%。

```html
<div class="img-wrapper">
  <img src="xxxxx" />
</div>

<style lang="scss">
  .img-wrapper {
    width: 100px;
    height: 100px;
    img {
      width: 100%;
      height: 100%;
    }
  }
</style>
```



## 参考

https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img