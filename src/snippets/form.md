---
title: HTML Form
mySlug: html form
tags:
  - HTML
  - CSS
created: 2022-06-06
updated: 2022-06-12T14:47:56.322Z
description: HTML 表单控件
---

## 什么是表单

HTML 表单和常规 HTML 文档的主要区别在于，大多数情况下，表单收集的数据被发送到 web 服务器。HMLT 表单是用户和 web 站点或应用程序之间交互的主要内容之一。

从用户体验的角度来看，要记住：**表单越大，失去用户的风险就越大。**

## 表单元素

- `<form>`
- `<fieldset>`
- `<legend>`
- `<textarea>`
- `<label>`
- `<button>`
- `<input>` 常见的 input 控件分类
  - text
  - button
  - checkbox
  - radio
  - password
  - file
  - image
  - hidden
  - reset
  - submit

## HTML5 input 类别

HTML5 最新的 `input` 控件提供内建的**客户端格式验证**（client-side validation）和在触摸设备下更好的**输入体验**（触摸设备可根据控件类型，展示不同的键盘）。

- `email` 类型可结合 `multiple` 属性使用，多个值需使用**英文逗号**分隔。触摸设备的键盘会展示 `@` 按键。
  ```html
  <input type="email" name="email" multiple />
  ```
- `tel` 电话号码类型。在触摸设备下，使用此控件会展示**电话号码键盘**。你可以使用 HMLT [pattern](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/pattern) 属性对输入值进行限制。
  ```html
  <input type="tel" name="tel" />
  ```
- `search` 与 `text` 类型相比主要区别是样式表现。它的样式在各主流浏览器下有不同的表现，比如有些版本的浏览器会展示一个清除内容的按钮。
  ```html
  <input type="search" name="search" />
  ```
- `url` 链接类型提供客户端检验，输入不是以 `http` 等协议（mail 协议除外）开头的链接会报告一个错误。触摸设备的键盘会显示 `/` 和 `.com` 等按键。
  ```html
  <input type="url" name="url" />
  ```
- `number` 数字类型。在触摸设备下，使用它输入内容会展示数字键盘，只允许输入浮点类型的数字。但默认情况下此控件输入值只能是整数，指定 `step` 的属性值为 `any` 或其他浮点数才能输入浮点类型的值。`step` 默认值为 1。

  ```html
  <!-- 输入浮点类型的值 step="any" -->
  <input type="numebr" name="number" step="any" />

  <!-- 输入浮点类型的值 step="0.1" -->
  <input type="numebr" name="number" step="0.1" />
  ```

  - `min` 和 `max` 属性可以指定最小和最大输入值。
  - `min` 和 `step` 的值会定义输入值的合法性，比如 `min="2.1"` 和 `step="2"`，合法的输入值有 2.1、4.1、6.1 等等必须是以 `.1` 结尾的偶数值，任何整数、奇数形式的 `.1` 和其他形式的浮点数都是非法值。参考 [min impact on step](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/step#min_impact_on_step)
    ```html
    <!-- 合法值：2.1, 4.1, 6.1, 8.1 等等 -->
    <!-- 非法值：整数和奇数形式的 3.1, 5.1, 6.1 以及其他不是 .1 结尾的浮点数-->
    <input type="number" min="2.1" step="2" />
    ```

- `range` 滑块控件。通常与 `min`、`max` 和 `step` 属性结合使用。
  
  ```html
  <input type="range" min="20" max="100" step="10" value="30"> 
  ```

### Date and time pickers

所有的日期和时间控件的值都可以使用 `min`、`max` 属性进行限制，也可以使用 `step` 属性进行更进一步的限制。

- `datetime-local`
- `month`
- `time`
- `week`
- `date`

## 多行文本控件（Multi-line text fields）

`<textarea>` 默认值在开启和关闭标签之间，而 `<input>` 是一个没有关闭标签空元素，它的默认值应该放在 `value` 属性中。

在非表单元素中使用 `contenteditable` 属性可以开启编辑功能。

HMTL 属性

- `cols`
- `rows`

CSS 属性

- `resize` - 调整输入框大小
  - `both` - 默认值
  - `horizontal`
  - `vertical`

```html
<textarea cols="30" rows="8">这里是 textarea 默认值</textarea>

<input type="text" value="这里是 input 的默认值" />

<div contenteditable>这是一个可编辑的 div 元素</div>
```

## 下拉选择控件

修改下拉控件的样式很难，因为它的内部结构很复杂，且在不同的浏览器中样式存在差异。

### 组成元素

- `<select>`
- `<option>`
- `<optgroup>` 结合 `label` 属性使用

### `<select>` 元素属性

- `name`
- `required`
- `disabled`
- `autocomplete`
- `autofocus`
- `size`
- `multiple`

```html
<div>
  <label for="simple-select">SimpleSelect</label>
  <select name="simple-select" id="simple-select">
    <option value="">--Please choose an option --</option>
    <option value="banana">Banana</option>
    <option value="cherry">Cherry</option>
    <option value="lemon">Lemon</option>
  </select>
</div>

<div>
  <label for="advanced-select">AdvancedSelect</label>
  <select name="advanced-select" id="advanced-select" multiple size="3">
    <optgroup label="fruits">
      <option value="banana">Banana</option>
      <option value="cherry">Cherry</option>
      <option value="lemon">Lemon</option>
    </optgroup>
    <optgroup label="vegetables">
      <option value="carrot">Carrot</option>
      <option value="eggplant">Eggplant</option>
      <option value="potato">Potato</option>
    </optgroup>
  </select>
</div>
```

## 自动补全的 input 控件

- `<input>` 结合 `list` 属性
- `<datalist>` 结合子元素 `<option>` 使用

```html
<div>
  <label for="myFruit">What's your favorite fruit?</label>
  <input type="text" name="myFruit" id="myFruit" list="mySuggestion" />
  <datalist id="mySuggestion">
    <option>Apple</option>
    <option>Banana</option>
    <option>Blackberry</option>
    <option>Blueberry</option>
    <option>Lemon</option>
    <option>Lychee</option>
    <option>Peach</option>
    <option>Pear</option>
  </datalist>
</div>
```

## Meters and progress bars

A process bar represents a value that changes over time up to a maximum values specified by the `max` attribute.

```html
<progress max="100" value="75">75/100</progress>
```

## 表单美化

表单控件有非常复杂的结构，除了修改一些基础的样式（比如改变宽度、外边距、边框），我们很难修改控件内部组件的样式。

如果你想要自定义表单控件，你必须通过 HTML、CSS 和 JavaScript 创建属于自己的表单控件或者使用第三方库。

根据调整表单控件样式的难易程度，可将表单元素分为三类：简单、中等、困难。**不要尝试修改分类为困难的表单控件，我认为这是在浪费时间，你应该自定义这部分控件或者使用第三方库代替。**

### 简单

调整这部分控件只需要很少的 CSS 规则。

- `<form>`
- `<fieldset>` 和 `<legend>`
- 单行文本输入 `<input type="text">`
- 多行 `<textarea>`
- 按钮
- `<label>`
- `<output>`

使用**字体和文本属性**

默认情况下，一些表单控件不会从它们的父元素继承 `font-family` 和 `font-size` 属性。许多的浏览器使用系统的默认表现代替。为了使表单的表现与其他内容保持一致，你可以在样式表中添加一下规则。

```css
button,
input,
select,
textare {
  font-family: inherit;
  font-size: 100%;
}
```

**legend placement**

`<legend>` 元素对于可访问性来说是非常重要的，辅助设备会读出它的内容，其的样式也容易调整。

```css
fieldset {
  position: relative;
}

legend {
  position: absolute;
  bottom: 0;
  right: 0;
}
```

### 中等
调整这部分控件需要编写大量的 CSS 规则，但修改的困难程度处于我们可控制的范围。首先你应该使用 `appearance: none;` 移除浏览器默认样式。

- 单选框和复选框
- `<input type="search">`

CSS `appearance` 属性控制着系统级别的样式。一般情况下 `appearance: none;` 会移除 `border` 的样式。

```css
-webkit-appearance: none;
appearance: none;
```

### 困难部分
调整这部分控件的样式很难达到我们满意的效果，因为我们没有能力去修改它们内部组件的样式。在生产环境中，建议使用自定义控件或者第三方库代替。

- `<input type="color">`
- 日期对应的控件
- `<input type="range">`
- `<input type="file">`
- `<select>` 、`<option>` 、`<progress>`、`<datalist>`
- `<progress>` 和 `<meter>`
- `<input type="number">` 调整数字大小的按钮, date 控件内部的组件，他们的样式不能通过 `appearance: none;` 被移除。
- `<input type="color">` 只能通过 CSS 移除此控件的 `border` 和 `padding` 属性。
- `<input type="range">` 你只能修改滑块控件的轨道样式，无法修改拖拽按钮的样式。
- `<input type="file">` 文件控件的按钮的样式不能被修改。你可以隐藏此按钮，通过相关联的 `<label>` 标签激活此按钮。比如：

  ```html
  <p>
    <label for="file">Choose a file</label>
    <input type="file" name="file" id="file">
  </p>
  ```

  ```css
  input[type='file'] {
    width: 0;
    height: 0;
    padding: 0;
    opacity: 0;
  }

  label[for='file'] {
    display: block;
    box-shadow: 1px 1px 3px #ccc;
    background: linear-gradient(to bottom, #eee, #ccc);
    border: 1px solid rbg(169, 169, 169);
    border-radius: 5px;
    text-align: center;
    line-height: 1.5;
  }
  ```

对于修改上面提到的控件样式，我们没有好的解决办法，但可以做一些基础的修改。比如添加下面的 CSS 重置规则：

```css
button,
label,
input,
select,
progress,
meter {
  display: block;
  font-family: inherit;
  font-size: 100%;
  margin: 0;
  box-sizing: border-box;
  width: 100%;
  padding: 5px;
  height: 30px;
}

input[type='color'],
input[type='datetime-local'],
input[type='text'],
select {
  box-shadow: inset 1px 1px 3px #ccc;
  border-radius: 5px;
}
```

## UI 伪类

使用伪类样式化表单控件。

- `:hover`
- `:focus`
- `:active`
- `:required` `:optional`
- `:valid` `:invalid` `:in-range` `:out-of-range`
- `:enabled` `:disabled` `:read-only` `:read-write`
- `:checked`

### :required 和 :optional

具有 required 属性的表单控件，匹配 `:required` ，其他不具有必选属性的控件，匹配 `:optional`

### :valid 和 :invalid（数据是否合法）

- 具有 `required` 属性的表单控件，如果没有输入任何值会被认为不合法，它们将匹配 `:invalid` 和 `:required`
- 使用 `min` 和 `max` 属性限制输入值，如果值在范围外，则会匹配 `:invalid` 和 `:out-of-range`
- 没有任何输入限制的表单控件，默认匹配 `:valid`

<p class="codepen" data-height="300" data-theme-id="dark" data-default-tab="html,result" data-slug-hash="GRQwxwq" data-preview="true" data-editable="true" data-user="byodian" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/byodian/pen/GRQwxwq">
  Blog - HTML form pseudo-classes</a> by byodian (<a href="https://codepen.io/byodian">@byodian</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

### :enabled 、:disabled 、:read-only 、:read-write（基于控件的状态）

`:read-only` 匹配使用 `readonly` 属性的 input 控件。

### 单选框和复选框的状态（checked、default、indeterminate）

- `:default` 匹配默认设置 `checked` 属性的单选或复选框
- `:indeterminate` 匹配既不是 checked 也不是 unchecked 状态的单选或者复选框。
  - `<input/radio>` 输入框，所有具有相同名称的单选框都处于未选中状态时
  - `<input/checkbox>` 复选框的 `indeterminate` 属性通过 JavaScript 设置为 `true` 时
  - `<process>` 元素没有值时

<p class="codepen" data-height="300" data-theme-id="dark" data-default-tab="html,result" data-slug-hash="eYVQweM" data-preview="true" data-editable="true" data-user="byodian" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/byodian/pen/eYVQweM">
  Blog - HTML Radio state pseudo-classes</a> by byodian (<a href="https://codepen.io/byodian">@byodian</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

## 客户端表单校验（client-side validation）

检查是否完成必填项的输入，输入值是否符合规定的格式。

### 两种校验方式

- 内建的表单校验。使用 HTML 表单校验特性，这些方式通常有比使用 JavaScript 更好的性能
- JavaScript 校验。

### 内建的表单校验（build-in form validation）

- requried
- minlength 和 maxlength 指定**文本类字符串**数据的长度
- min 和 max 指定**数字 input 类型**值的最小和最大值
- pattern 指定一个正则表达式

当一个表单选项数据是合法值时，它将匹配 `:valid` CSS 伪类元素，你可以使用它为合法的元素指定样式。

当一个表单选项的数据是非法值时，它将匹配 `:invalid` CSS 伪类元素，有时也会匹配其他伪类元素，比如 `:out-of-range` 。

DOM 接口 [ValidityState](https://developer.mozilla.org/en-US/docs/Web/API/ValidityState) 提供了多种错误方式，阻止表单的提交

- badInput
- patternMismatch
- rangeOverflow/rangeUnderflow
- stepMismatch
- tooLong/tooShort
- typeMismatch
- valueMissing/customError

### 使用 JavaScript 校验表单

如果你想控制错误信息的样式或者兼容不支持 HTML 内建表单验证的浏览器，你可以使用 JavaScrpt 的方式校验表单。

使用 **[Constraint validation API](https://developer.mozilla.org/en-US/docs/Web/API/Constraint_validation)** 检验输入值。

## 第三方库

### 框架

- [uni-form](https://github.com/draganbabic/uni-form)
- [Formalize](https://formalize.me/)

### 处理 HTML 表单控件

- [jQuery UI](https://jqueryui.com/)
- [Bootstrap](https://getbootstrap.com/docs/5.1/forms/overview/) can help normalize your forms.
- [WebShim](https://afarkas.github.io/webshim/demos/) is a huge tool that can help you deal with browser HTML5 support. The web forms part can be really helpful.

## References

- [An Extensive Guide To Web Form Usability](https://www.smashingmagazine.com/2011/11/extensive-guide-web-form-usability/)
- [7 Basic Best Practices for Buttons](https://www.uxmatters.com/mt/archives/2012/05/7-basic-best-practices-for-buttons.php)
- [Pagination in Web Forms](https://www.uxmatters.com/mt/archives/2010/03/pagination-in-web-forms-evaluating-the-effectiveness-of-web-forms.php)
- [Web forms — Working with user data](https://developer.mozilla.org/en-US/docs/Learn/Forms)
- [uxdesign-forms](https://uxdesign.smashingmagazine.com/category/forms)
