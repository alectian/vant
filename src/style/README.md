# Built-in Style

### Intro

icloudata contains some common styles that can be used directly by the className.

### Text ellipsis

When the text content length exceeds the maximum container width, the excess text is automatically omitted.

```html
<div class="icloudata-ellipsis">
  This is a paragraph that displays up to one line of text, and the rest of the
  text will be omitted.
</div>

<div class="icloudata-multi-ellipsis--l2">
  This is a paragraph that displays up to two lines of text, and the rest of the
  text will be omitted.
</div>

<div class="icloudata-multi-ellipsis--l3">
  This is a paragraph that displays up to three lines of text, and the rest of
  the text will be omitted.
</div>
```

### Hairline

Add 1px border under the Retina screen for the element, based on a pseudo element.

```html
<!-- border top -->
<div class="icloudata-hairline--top"></div>

<!-- border bottom -->
<div class="icloudata-hairline--bottom"></div>

<!-- border left -->
<div class="icloudata-hairline--left"></div>

<!-- border right -->
<div class="icloudata-hairline--right"></div>

<!-- border top & bottom -->
<div class="icloudata-hairline--top-bottom"></div>

<!-- full border -->
<div class="icloudata-hairline--surround"></div>
```

### Animation

```html
<!-- fade in  -->
<transition name="icloudata-fade">
  <div v-show="visible">Fade</div>
</transition>

<!-- slide up -->
<transition name="icloudata-slide-up">
  <div v-show="visible">Slide Up</div>
</transition>

<!-- slide down -->
<transition name="icloudata-slide-down">
  <div v-show="visible">Slide Down</div>
</transition>

<!-- slide left -->
<transition name="icloudata-slide-left">
  <div v-show="visible">Slide Left</div>
</transition>

<!-- slide right -->
<transition name="icloudata-slide-right">
  <div v-show="visible">Slide Right</div>
</transition>
```
