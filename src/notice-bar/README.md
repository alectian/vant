# NoticeBar

### Install

```js
import { createApp } from 'vue';
import { NoticeBar } from 'cloudata';

const app = createApp();
app.use(NoticeBar);
```

## Usage

### Basic Usage

```html
<icloudata-notice-bar text="Notice Content" left-icon="volume-o" />
```

### Scrollable

```html
<!-- Enable scroll when text is short -->
<icloudata-notice-bar scrollable text="Notice Content" />

<!-- Disable scroll when text is long -->
<icloudata-notice-bar
  :scrollable="false"
  text="Technology is the common soul of the people who developed it."
/>
```

### Wrapable

```html
<icloudata-notice-bar wrapable :scrollable="false">Notice Content</icloudata-notice-bar>
```

### Mode

```html
<icloudata-notice-bar mode="closeable">Notice Content</icloudata-notice-bar>

<icloudata-notice-bar mode="link">Notice Content</icloudata-notice-bar>
```

### Custom Style

```html
<icloudata-notice-bar color="#1989fa" background="#ecf9ff" left-icon="info-o">
  Notice Content
</icloudata-notice-bar>
```

### Vertical Scroll

```html
<icloudata-notice-bar left-icon="volume-o" :scrollable="false">
  <icloudata-swipe
    vertical
    class="notice-swipe"
    :autoplay="3000"
    :show-indicators="false"
  >
    <icloudata-swipe-item>Content 1</icloudata-swipe-item>
    <icloudata-swipe-item>Content 2</icloudata-swipe-item>
    <icloudata-swipe-item>Content 3</icloudata-swipe-item>
  </icloudata-swipe>
</icloudata-notice-bar>

<style>
  .notice-swipe {
    height: 40px;
    line-height: 40px;
  }
</style>
```

## API

### Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| mode | Mode, can be set to `closeable` `link` | _string_ | `''` |
| text | Notice text content | _string_ | `''` | - |
| color | Text color | _string_ | `#f60` |
| background | Background color | _string_ | `#fff7cc` |
| left-icon | Left Icon | _string_ | - |
| delay | Animation delay (s) | _number \| string_ | `1` |
| speed | Scroll speed (px/s) | _number \| string_ | `50` |
| scrollable | Whether to scroll content | _boolean_ | - |
| wrapable | Whether to enable text wrap | _boolean_ | `false` | - |

### Events

| Event           | Description                        | Arguments      |
| --------------- | ---------------------------------- | -------------- |
| click           | Emitted when NoticeBar is clicked  | _event: Event_ |
| close           | Emitted when NoticeBar is closed   | _event: Event_ |
| replay `v2.6.2` | Emitted when NoticeBar is replayed | -              |

### Slots

| Name       | Description         |
| ---------- | ------------------- |
| default    | Notice text content |
| left-icon  | Custom left icon    |
| right-icon | Custom right icon   |

### Less Variables

How to use: [Custom Theme](#/en-US/theme).

| Name                         | Default Value             | Description |
| ---------------------------- | ------------------------- | ----------- |
| @notice-bar-height           | `40px`                    | -           |
| @notice-bar-padding          | `0 @padding-md`           | -           |
| @notice-bar-wrapable-padding | `@padding-xs @padding-md` | -           |
| @notice-bar-text-color       | `@orange-dark`            | -           |
| @notice-bar-font-size        | `@font-size-md`           | -           |
| @notice-bar-line-height      | `24px`                    | -           |
| @notice-bar-background-color | `@orange-light`           | -           |
| @notice-bar-icon-size        | `16px`                    | -           |
| @notice-bar-icon-min-width   | `24px`                    | -           |
