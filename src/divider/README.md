# Divider

### Install

```js
import { createApp } from 'vue';
import { Divider } from 'cloudata';

const app = createApp();
app.use(Divider);
```

## Usage

### Basic Usage

```html
<icloudata-divider />
```

### With Text

```html
<icloudata-divider>Text</icloudata-divider>
```

### Content Position

```html
<icloudata-divider content-position="left">Text</icloudata-divider>
<icloudata-divider content-position="right">Text</icloudata-divider>
```

### Dashed

```html
<icloudata-divider dashed>Text</icloudata-divider>
```

### Custom Style

```html
<icloudata-divider
  :style="{ color: '#1989fa', borderColor: '#1989fa', padding: '0 16px' }"
>
  Text
</icloudata-divider>
```

## API

### Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| dashed | Whether to use dashed border | _boolean_ | `false` |
| hairline | Whether to use hairline | _boolean_ | `true` |
| content-position | Content position，can be set to `left` `right` | _string_ | `center` |

### Slots

| Name    | Description |
| ------- | ----------- |
| default | content     |

### Less Variables

How to use: [Custom Theme](#/en-US/theme).

| Name                         | Default Value   | Description |
| ---------------------------- | --------------- | ----------- |
| @divider-margin              | `@padding-md 0` | -           |
| @divider-text-color          | `@gray-6`       | -           |
| @divider-font-size           | `@font-size-md` | -           |
| @divider-line-height         | `24px`          | -           |
| @divider-border-color        | `@border-color` | -           |
| @divider-content-padding     | `@padding-md`   | -           |
| @divider-content-left-width  | `10%`           | -           |
| @divider-content-right-width | `10%`           | -           |
