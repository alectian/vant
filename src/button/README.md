# Button

### Install

```js
import { createApp } from 'vue';
import { Button } from 'cloudata';

const app = createApp();
app.use(Button);
```

## Usage

### Type

```html
<icloudata-button type="primary">Primary</icloudata-button>
<icloudata-button type="success">Success</icloudata-button>
<icloudata-button type="default">Default</icloudata-button>
<icloudata-button type="danger">Danger</icloudata-button>
<icloudata-button type="warning">Warning</icloudata-button>
```

### Plain

```html
<icloudata-button plain type="primary">Primary</icloudata-button>
<icloudata-button plain type="primary">Danger</icloudata-button>
```

### Hairline

```html
<icloudata-button plain hairline type="primary">Hairline</icloudata-button>
<icloudata-button plain hairline type="primary">Hairline</icloudata-button>
```

### Disabled

```html
<icloudata-button disabled type="primary">Diabled</icloudata-button>
<icloudata-button disabled type="primary">Diabled</icloudata-button>
```

### Loading

```html
<icloudata-button loading type="primary" />
<icloudata-button loading type="primary" loading-type="spinner" />
<icloudata-button loading type="primary" loading-text="Loading..." />
```

### Shape

```html
<icloudata-button square type="primary">Square</icloudata-button>
<icloudata-button round type="primary">Round</icloudata-button>
```

### Icon

```html
<icloudata-button icon="plus" type="primary" />
<icloudata-button icon="plus" type="primary">Button</icloudata-button>
<icloudata-button icon="https://img.yzcdn.cn/vant/user-active.png" type="primary">
  Button
</icloudata-button>
```

### Size

```html
<icloudata-button type="primary" size="large">Large</icloudata-button>
<icloudata-button type="primary" size="normal">Normal</icloudata-button>
<icloudata-button type="primary" size="small">Small</icloudata-button>
<icloudata-button type="primary" size="mini">Mini</icloudata-button>
```

### Block Element

```html
<icloudata-button type="primary" block>Block Element</icloudata-button>
```

### Route

```html
<icloudata-button type="primary" url="/vant/mobile.html">URL</icloudata-button>
<icloudata-button type="primary" to="index">Vue Router</icloudata-button>
```

### Custom Color

```html
<icloudata-button color="#7232dd">Pure</icloudata-button>
<icloudata-button color="#7232dd" plain>Pure</icloudata-button>
<icloudata-button color="linear-gradient(to right, #ff6034, #ee0a24)">
  Gradient
</icloudata-button>
```

## API

### Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| type | Can be set to `primary` `success` `warning` `danger` | _string_ | `default` |
| size | Can be set to `large` `small` `mini` | _string_ | `normal` |
| text | Text | _string_ | - |
| color | Color, support linear-gradient | _string_ | - |
| icon | Left Icon | _string_ | - |
| icon-prefix `v2.6.0` | Icon className prefix | _string_ | `van-icon` |
| icon-position `v2.10.7` | Icon position, can be set to `right` | _string_ | `left` |
| tag | HTML Tag | _string_ | `button` |
| native-type | Native Type Attribute | _string_ | `button` |
| plain | Whether to be plain button | _boolean_ | `false` |
| block | Whether to set display block | _boolean_ | `false` |
| round | Whether to be round button | _boolean_ | `false` |
| square | Whether to be square button | _boolean_ | `false` |
| disabled | Whether to disable button | _boolean_ | `false` |
| loading | Whether show loading status | _boolean_ | `false` |
| loading-text | Loading text | _string_ | - |
| loading-type | Loading type, can be set to `spinner` | _string_ | `circular` |
| loading-size | Loading icon size | _string_ | `20px` |
| url | Link URL | _string_ | - |
| to | Target route of the link, same as using vue-router | _string \| object_ | - |
| replace | If true, the navigation will not leave a history record | _boolean_ | `false` |

### Events

| Event | Description | Arguments |
| --- | --- | --- |
| click | Emitted when button is clicked and not disabled or loading | _event: Event_ |
| touchstart | Emitted when button is touched | _event: TouchEvent_ |

### Slots

| Name              | Description         |
| ----------------- | ------------------- |
| default           | Default slot        |
| loading `v2.10.1` | Custom loading icon |

### Less Variables

How to use: [Custom Theme](#/en-US/theme).

| Name                             | Default Value        | Description |
| -------------------------------- | -------------------- | ----------- |
| @button-mini-height              | `24px`               | -           |
| @button-mini-font-size           | `@font-size-xs`      | -           |
| @button-small-height             | `32px`               | -           |
| @button-small-font-size          | `@font-size-sm`      | -           |
| @button-normal-font-size         | `@font-size-md`      | -           |
| @button-large-height             | `50px`               | -           |
| @button-default-height           | `44px`               | -           |
| @button-default-line-height      | `1.2`                | -           |
| @button-default-font-size        | `@font-size-lg`      | -           |
| @button-default-color            | `@text-color`        | -           |
| @button-default-background-color | `@white`             | -           |
| @button-default-border-color     | `@border-color`      | -           |
| @button-primary-color            | `@white`             | -           |
| @button-primary-background-color | `@blue`              | -           |
| @button-primary-border-color     | `@blue`              | -           |
| @button-success-color            | `@white`             | -           |
| @button-success-background-color | `@green`             | -           |
| @button-success-border-color     | `@green`             | -           |
| @button-danger-color             | `@white`             | -           |
| @button-danger-background-color  | `@red`               | -           |
| @button-danger-border-color      | `@red`               | -           |
| @button-warning-color            | `@white`             | -           |
| @button-warning-background-color | `@orange`            | -           |
| @button-warning-border-color     | `@orange`            | -           |
| @button-border-width             | `@border-width-base` | -           |
| @button-border-radius            | `@border-radius-sm`  | -           |
| @button-round-border-radius      | `@border-radius-max` | -           |
| @button-plain-background-color   | `@white`             | -           |
| @button-disabled-opacity         | `@disabled-opacity`  | -           |
