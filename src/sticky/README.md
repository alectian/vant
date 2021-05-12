# Sticky

### Install

```js
import { createApp } from 'vue';
import { Sticky } from 'cloudata';

const app = createApp();
app.use(Sticky);
```

## Usage

### Basic Usage

```html
<icloudata-sticky>
  <icloudata-button type="primary">Basic Usage</icloudata-button>
</icloudata-sticky>
```

### Offset Top

```html
<icloudata-sticky :offset-top="50">
  <icloudata-button type="primary">Offset Top</icloudata-button>
</icloudata-sticky>
```

### Set Container

```html
<div ref="container" style="height: 150px;">
  <icloudata-sticky :container="container">
    <icloudata-button type="warning">Set Container</icloudata-button>
  </icloudata-sticky>
</div>
```

```js
export default {
  setup() {
    const container = ref(null);
    return { container };
  },
};
```

## API

### Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| offset-top `v2.8.7` | Offset top, supports `px` `vw` `vh` `rem` unit, default `px` | _number \| string_ | `0` |
| z-index | z-index when sticky | _number \| string_ | `99` |
| container | Container DOM | _Element_ | - |

### Events

| Event  | Description            | Arguments                      |
| ------ | ---------------------- | ------------------------------ |
| scroll | Emitted when scrolling | object: { scrollTop, isFixed } |

### Less Variables

How to use: [Custom Theme](#/en-US/theme).

| Name            | Default Value | Description |
| --------------- | ------------- | ----------- |
| @sticky-z-index | `99`          | -           |
