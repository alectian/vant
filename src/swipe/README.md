# Swipe

### Install

```js
import { createApp } from 'vue';
import { Swipe, SwipeItem } from 'cloudata';

const app = createApp();
app.use(Swipe);
app.use(SwipeItem);
```

## Usage

### Basic Usage

Use `autoplay` prop to set autoplay interval.

```html
<icloudata-swipe class="my-swipe" :autoplay="3000" indicator-color="white">
  <icloudata-swipe-item>1</icloudata-swipe-item>
  <icloudata-swipe-item>2</icloudata-swipe-item>
  <icloudata-swipe-item>3</icloudata-swipe-item>
  <icloudata-swipe-item>4</icloudata-swipe-item>
</icloudata-swipe>

<style>
  .my-swipe .icloudata-swipe-item {
    color: #fff;
    font-size: 20px;
    line-height: 150px;
    text-align: center;
    background-color: #39a9ed;
  }
</style>
```

### Lazy Render

Use `lazy-render` prop to enable lazy rendering.

```html
<icloudata-swipe :autoplay="3000" lazy-render>
  <icloudata-swipe-item v-for="image in images" :key="image">
    <img :src="image" />
  </icloudata-swipe-item>
</icloudata-swipe>
```

```js
export default {
  setup() {
    const images = [
      'https://img.yzcdn.cn/vant/apple-1.jpg',
      'https://img.yzcdn.cn/vant/apple-2.jpg',
    ];
    return { images };
  },
};
```

### Change Event

```html
<icloudata-swipe @change="onChange">
  <icloudata-swipe-item>1</icloudata-swipe-item>
  <icloudata-swipe-item>2</icloudata-swipe-item>
  <icloudata-swipe-item>3</icloudata-swipe-item>
  <icloudata-swipe-item>4</icloudata-swipe-item>
</icloudata-swipe>
```

```js
import { Toast } from 'cloudata';

export default {
  setup() {
    const onChange = (index) => {
      Toast('Current Swipe index:' + index);
    };
    return { onChange };
  },
};
```

### Vertical Scrolling

```html
<icloudata-swipe :autoplay="3000" vertical>
  <icloudata-swipe-item>1</icloudata-swipe-item>
  <icloudata-swipe-item>2</icloudata-swipe-item>
  <icloudata-swipe-item>3</icloudata-swipe-item>
  <icloudata-swipe-item>4</icloudata-swipe-item>
</icloudata-swipe>
```

### Set SwipeItem Size

```html
<icloudata-swipe :loop="false" :width="300">
  <icloudata-swipe-item>1</icloudata-swipe-item>
  <icloudata-swipe-item>2</icloudata-swipe-item>
  <icloudata-swipe-item>3</icloudata-swipe-item>
  <icloudata-swipe-item>4</icloudata-swipe-item>
</icloudata-swipe>
```

> It's not supported to set SwipeItem size in the loop mode.

### Custom Indicator

```html
<icloudata-swipe @change="onChange">
  <icloudata-swipe-item>1</icloudata-swipe-item>
  <icloudata-swipe-item>2</icloudata-swipe-item>
  <icloudata-swipe-item>3</icloudata-swipe-item>
  <icloudata-swipe-item>4</icloudata-swipe-item>
  <template #indicator>
    <div class="custom-indicator">{{ current + 1 }}/4</div>
  </template>
</icloudata-swipe>

<style>
  .custom-indicator {
    position: absolute;
    right: 5px;
    bottom: 5px;
    padding: 2px 5px;
    font-size: 12px;
    background: rgba(0, 0, 0, 0.1);
  }
</style>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const current = ref(0);
    const onChange = (index) => {
      current.value = index;
    };
    return {
      current,
      onChange,
    };
  },
};
```

## API

### Swipe Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| autoplay | Autoplay interval (ms) | _number \| string_ | - |
| duration | Animation duration (ms) | _number \| string_ | `500` |
| initial-swipe | Index of initial swipe, start from 0 | _number \| string_ | `0` |
| width | Set Swiper Item Width | _number \| string_ | `0` |
| height | Set Swiper Item Height | _number \| string_ | `0` |
| loop | Whether to enable loop | _boolean_ | `true` |
| show-indicators | Whether to show indicators | _boolean_ | `true` |
| vertical | Whether to be vertical Scrolling | _boolean_ | `false` |
| touchable | Whether to allow swipe by touch gesture | _boolean_ | `true` |
| stop-propagation | Whether to stop touchmove event propagation | _boolean_ | `false` |
| lazy-render `v2.5.8` | Whether to enable lazy render | _boolean_ | `false` |
| indicator-color | Indicator color | _string_ | `#1989fa` |

### Swipe Events

| Event  | Description                        | Arguments                     |
| ------ | ---------------------------------- | ----------------------------- |
| change | Emitted when current swipe changed | index: index of current swipe |

### SwipeItem Events

| Event | Description                       | Arguments      |
| ----- | --------------------------------- | -------------- |
| click | Emitted when component is clicked | _event: Event_ |

### Swipe Methods

Use [ref](https://v3.vuejs.org/guide/component-template-refs.html) to get Swipe instance and call instance methods..

| Name | Description | Attribute | Return value |
| --- | --- | --- | --- |
| prev `v2.4.2` | Swipe to prev item | - | - |
| next `v2.4.2` | Swipe to next item | - | - |
| swipeTo | Swipe to target index | index: target index, options: Options | - |
| resize | Resize Swipe when container element resized or visibility changed | - | - |

### swipeTo Options

| Name      | Description               | Type      |
| --------- | ------------------------- | --------- |
| immediate | Whether to skip animation | _boolean_ |

### Swipe Slots

| Name      | Description      |
| --------- | ---------------- |
| default   | Content          |
| indicator | Custom indicator |

### Less Variables

How to use: [Custom Theme](#/en-US/theme).

| Name                                       | Default Value   | Description |
| ------------------------------------------ | --------------- | ----------- |
| @swipe-indicator-size                      | `6px`           | -           |
| @swipe-indicator-margin                    | `@padding-sm`   | -           |
| @swipe-indicator-active-opacity            | `1`             | -           |
| @swipe-indicator-inactive-opacity          | `0.3`           | -           |
| @swipe-indicator-active-background-color   | `@blue`         | -           |
| @swipe-indicator-inactive-background-color | `@border-color` | -           |
