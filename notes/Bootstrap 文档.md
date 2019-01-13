# Bootstrap 文档

## Grid

1.grid 样式是基于flexbox建立的。

### flexbox:  

#### 设置对应的两个axes of flexbox

设定对应container display: flex/inline-flex;

> 对应的初始状态：

> - Items display in a row (the `flex-direction` property's default is `row`).
> - The items start from the start edge of the main axis.
> - The items do not stretch on the main dimension, but can shrink.
> - The items will stretch to fill the size of the cross axis.
> - The [`flex-basis`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis) property is set to `auto`.
> - The [`flex-wrap`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-wrap) property is set to `nowrap`.

1. 排列成一行；
2. 以他们本身内容的size为main axis的size；
3. 如果items太多，会溢出，不会wrap；
4. 如果一个item高于其他，其他的会自动填满Cross Axis；
5. 不会延展，但可以缩小



#### The flex container 

可能遇到的场景：



1. 元素太多，会溢出，可以使用flex-wrap: wrap.//flex-flow: row wrap;

2. 设置元素宽度，等等，使用flex shorthand:  

   flex-grow(如何按比例分配剩余空间), 

   flex-shrink(设为正值，目前为1), 

   flex-basis(显示的宽度 初始值为auto，为内容宽度)

3. 初始值为flex: 0 1 auto



#### Alignment,justification and distribution of free space between items

align-items: 设定cross axis 对应的值。==初始值为: stretch==. 

​                      这是为什么所有元素都会随着最高的那个拉伸；

​                      可以设定的值： stretch/flex-start/flex-end/center

justify-content: 在main axis上设定items,==初始值为flex-start==;

​                          可以设定的值：flex-start, flex-end, center, space-around, space-between, space-evenly

​                          下图为space-evenly.   

![1544004575161](C:\Users\Xiaozhou Huangfu\AppData\Roaming\Typora\typora-user-images\1544004575161.png)



#### 总结

summary: flexbox:

- [x] flexbox 分为main axes 和 cross axes 两个属性可以分别设定；
- [x] flex container 内部的各种初始值及特性上面引用可见；
- [x] flex container 存在需要设定wrap属性的情况
- [x] flex-flow 有三个值可以一起设定，主要用来处理剩余空间，包括剩余空间分配， 缩小指数，元素的宽度，上面案例可见；
- [x] main axes 和cross axes的排列方向，样式，居中等设置，main axes: align-items; cross axes 为justify-content. 具体属性值由上可见

### How grid system works

#### 如何书写

![1544065241346](C:\Users\Xiaozhou Huangfu\AppData\Roaming\Typora\typora-user-images\1544065241346.png)

```html
<div class="container">
  <div class="row">
    <div class="col-sm">
      One of three columns
    </div>
    <div class="col-sm">
      One of three columns
    </div>
    <div class="col-sm">
      One of three columns
    </div>
  </div>
</div>
```

#### 如何实现

将在不同大小的屏幕上显示为三个等分列:

1. .container, 将内容放置在container中间，竖直摆放;如果使用.container-fluid & width: 100%， 全屏展示；
2. rows 用来包裹columns， 每个column都有水平的padding,与rows的负margin抵消以后，效果为靠左显示；
3. 要达到上面的效果，row必须直接包裹col;
4. 如果没有预设宽度，所有col的宽度将会均等分配；
5. 预设宽度的使用方法：预设分为n=12等分，指定宽度为 .col-n;
6. col的宽度是百分比设定的；
7. col的原始效果是靠左显示，但如果拿走rows的margin,和column的padding,效果就会变成.no-gutter；
8. grid的自相应设置有5个设置点； 应用形式为已最小宽度为基准向上。

#### Grid的自相应选项

![1545363323509](C:\Users\Xiaozhou Huangfu\AppData\Roaming\Typora\typora-user-images\1545363323509.png)

#### 一些其他的应用场景

1. 设定某一个col的值： class = “col-6”;
2. 根据内容的宽度觉得col宽度：col-{breakpoint}-auto;
3. 设定多行显示: 在需跳行处添加：.w-100;

#### 多个类的叠加

依次添加多个类则可以达到在不同的屏幕大小，不同的显示结果：

```html
<!-- Stack the columns on mobile by making one full-width and the other half-width -->
<div class="row">
  <div class="col-12 col-md-8">.col-12 .col-md-8</div>
  <div class="col-6 col-md-4">.col-6 .col-md-4</div>
</div>

<!-- Columns start at 50% wide on mobile and bump up to 33.3% wide on desktop -->
<div class="row">
  <div class="col-6 col-md-4">.col-6 .col-md-4</div>
  <div class="col-6 col-md-4">.col-6 .col-md-4</div>
  <div class="col-6 col-md-4">.col-6 .col-md-4</div>
</div>

<!-- Columns are always 50% wide, on mobile and desktop -->
<div class="row">
  <div class="col-6">.col-6</div>
  <div class="col-6">.col-6</div>
</div>
```

#### 对齐

##### 垂直方向的对齐

三种方式：align-self-start, 

​                     align-self-center, 

​		     align-self-end;

效果：

![1545372841728](C:\Users\Xiaozhou Huangfu\AppData\Roaming\Typora\typora-user-images\1545372841728.png)

```html
<div class="container">
  <div class="row">
    <div class="col align-self-start">
      One of three columns
    </div>
    <div class="col align-self-center">
      One of three columns
    </div>
    <div class="col align-self-end">
      One of three columns
    </div>
  </div>
</div>
```

##### 水平方向的对齐

五种对齐方式： 

1. justify-content-start, 
2. justify-content-center, 
3. justify-content-end,
4. justify-content-around,
5. justify-content-between,

从上至下，依次效果：

![1545374292032](C:\Users\Xiaozhou Huangfu\AppData\Roaming\Typora\typora-user-images\1545374292032.png)

##### 前端内容不留白对齐

前端不留白可以通过.no-gutters 来实现。

实现的方式：

 

```sass
.no-gutters {
  margin-right: 0;
  margin-left: 0;

  > .col,
  > [class*="col-"] {
    padding-right: 0;
    padding-left: 0;
  }
}
```

![1545374781324](C:\Users\Xiaozhou Huangfu\AppData\Roaming\Typora\typora-user-images\1545374781324.png)



```html
<div class="row no-gutters">
  <div class="col-12 col-sm-6 col-md-8">.col-12 .col-sm-6 .col-md-8</div>
  <div class="col-6 col-md-4">.col-6 .col-md-4</div>
</div>
```

##### 自动换行

当规定了col的宽度，类似：col-6,col-8, etc...

当相加超过12，自动跳行





##### 多种形式的跳行

跳行的这一特性可以通过设置具体的breakpoint来实现只在这个breakpoint完成跳行：

例如如下语句：

```html
<div class="row">
  <div class="col-6 col-sm-4">.col-6 .col-sm-4</div>
  <div class="col-6 col-sm-4">.col-6 .col-sm-4</div>

  <!-- Force next columns to break to new line at md breakpoint and up -->
  <div class="w-100 d-none d-md-block"></div>

  <div class="col-6 col-sm-4">.col-6 .col-sm-4</div>
  <div class="col-6 col-sm-4">.col-6 .col-sm-4</div>
</div>
```

1. 在xs最小屏幕时，不会应用跳行，效果为：在整个屏幕上平分：


![1545376496014](C:\Users\Xiaozhou Huangfu\AppData\Roaming\Typora\typora-user-images\1545376496014.png)

2. 在s屏幕时，变为三个平分，依然不会跳行：

   ![1545376570575](C:\Users\Xiaozhou Huangfu\AppData\Roaming\Typora\typora-user-images\1545376570575.png)



3. 当屏幕延展为md时，实现跳行：

   ![1545376644917](C:\Users\Xiaozhou Huangfu\AppData\Roaming\Typora\typora-user-images\1545376644917.png)

#### Reordering重新排序

##### 类的排序 Order classes

可以通过.order- 来进行排序。若没有指明排序的位置，那么原地不动；

order顺序的范围从1-12；

也可以在此之外添加： .order-first, .order-last来实现-1，和13的两个排序位置；



##### col的位移offset columns

使用方法： .offset-md-*; *指的是左边空出来的位数。例如：.offset-md-3，左边偏移三个个数。

需要注意的是，有时会在某一个屏幕大小设置偏移，那么设置完毕，在下一个大小设置时需要重新设置：

例如：class = “col-sm-5 ==offset-sm-2== col-md-6 ==off-set-md-0==”;



```html
<div class="row">
  <div class="col-sm-5 col-md-6">.col-sm-5 .col-md-6</div>
  <div class="col-sm-5 offset-sm-2 col-md-6 offset-md-0">.col-sm-5 .offset-sm-2 .col-md-6 .offset-md-0</div>
</div>

<div class="row">
  <div class="col-sm-6 col-md-5 col-lg-6">.col-sm-6 .col-md-5 .col-lg-6</div>
  <div class="col-sm-6 col-md-5 offset-md-2 col-lg-6 offset-lg-0">.col-sm-6 .col-md-5 .offset-md-2 .col-lg-6 .offset-lg-0</div>
</div>
```

#### 嵌套

col和row可以进行嵌套；嵌套方法就是直接讲下一级的row嵌套进入上一级的col



#### SASS mixins

## Media Object



有一些区域是含媒体文件的区域，同样可以用bootstrap给定的信息进行完成。使用方法很简单，只需两个属性： ==.media==（用来包裹整个区域）==.media-body== （用来包裹其他内容。如果需要调整padding和margin则用spacing utilities 里的属性来实现。



### 嵌套

按照.media + .media-body一组的方法，可以进行嵌套



### 排序

可以通过调整html文件本身，或者调整 .order属性来调整区域内的显示顺序（例如：媒体文件的左右）



### 队列

.media + .media-body 同样可以适用于列表式展示：

1. 在<ul>/<ol>  上加入.list-unstyled的属性去掉自带属性;
2. 在<li>中填入.media + .media-body元素。





## Utilties for layout



如何更好的实现自响应 => 有一些没有设定自响应的元素，可以通过自己设定来实现：

###  更改display 属性

如果需要更改成flex，则应添加：.d-flex 或者.d-{breakpoint}-flex;



### 其他flexbox属性

如果有其他的flexbox 属性需要更改，例如： sizing, spacing, and more。可以参考 flexbox utilities 来进行相应的更新：

#### 通过更新d-flex/d-inline-flex 来更新子组件为一个flex container

可以不加breakpoint/加breakpoint:

- `.d-flex`
- `.d-inline-flex`
- `.d-sm-flex`
- `.d-sm-inline-flex`
- `.d-md-flex`
- `.d-md-inline-flex`
- `.d-lg-flex`
- `.d-lg-inline-flex`
- `.d-xl-flex`
- `.d-xl-inline-flex`



#### 方向的变化









