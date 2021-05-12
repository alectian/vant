# Tab

### Install

```js
import { createApp } from 'vue';
import { Tab, Tabs } from 'cloudata';

const app = createApp();
app.use(Tab);
app.use(Tabs);
```

## Usage

### Basic Usage

The first tab is actived by default, you can set `v-model:active` to active specified tab.

```html
<icloudata-tabs v-model:active="active">
  <icloudata-tab v-for="index in 4" :title="'tab' + index">
    content of tab {{ index }}
  </icloudata-tab>
</icloudata-tabs>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const active = ref(2);
    return { active };
  },
};
```

### Match By Name

```html
<icloudata-tabs v-model:active="activeName">
  <icloudata-tab title="tab 1" name="a">content of tab 1</icloudata-tab>
  <icloudata-tab title="tab 2" name="b">content of tab 2</icloudata-tab>
  <icloudata-tab title="tab 3" name="c">content of tab 3</icloudata-tab>
</icloudata-tabs>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const activeName = ref('a');
    return { activeName };
  },
};
```

### Swipe Tabs

By default more than 5 tabs, you can scroll through the tabs. You can set `swipe-threshold` attribute to customize threshold number.

```html
<icloudata-tabs>
  <icloudata-tab v-for="index in 8" :title="'tab' + index">
    content of tab {{ index }}
  </icloudata-tab>
</icloudata-tabs>
```

### Disabled Tab

You can set `disabled` attribute on the corresponding `icloudata-tab`.

```html
<icloudata-tabs @disabled="onClickDisabled">
  <icloudata-tab v-for="index in 3" :title="'tab' + index" :disabled="index === 2">
    content of tab {{ index }}
  </icloudata-tab>
</icloudata-tabs>
```

```js
import { Toast } from 'cloudata';

export default {
  setup() {
    const onClickDisabled = (name, title) => {
      Toast(name + ' is disabled');
    };

    return {
      onClickDisabled,
    };
  },
};
```

### Card Style

Tabs styled as cards.

```html
<icloudata-tabs type="card">
  <icloudata-tab v-for="index in 3" :title="'tab' + index">
    content of tab {{ index }}
  </icloudata-tab>
</icloudata-tabs>
```

### Click Event

```html
<icloudata-tabs @click="onClick">
  <icloudata-tab v-for="index in 2" :title="'tab' + index">
    content of tab {{ index }}
  </icloudata-tab>
</icloudata-tabs>
```

```js
import { Toast } from 'cloudata';

export default {
  setup() {
    const onClick = (name, title) => {
      Toast(title);
    };

    return {
      onClick,
    };
  },
};
```

### Sticky

In sticky mode, the tab will be fixed to top when scroll to top.

```html
<icloudata-tabs v-model:active="active" sticky>
  <icloudata-tab v-for="index in 4" :title="'tab ' + index">
    content {{ index }}
  </icloudata-tab>
</icloudata-tabs>
```

### Custom title

Use title slot to custom tab title.

```html
<icloudata-tabs v-model:active="active">
  <icloudata-tab v-for="index in 2" :key="index">
    <template #title> <icloudata-icon name="more-o" />tab </template>
    content {{ index }}
  </icloudata-tab>
</icloudata-tabs>
```

### Switch Animation

Use `animated` props to change tabs with animation.

```html
<icloudata-tabs v-model:active="active" animated>
  <icloudata-tab v-for="index in 4" :title="'tab ' + index">
    content {{ index }}
  </icloudata-tab>
</icloudata-tabs>
```

### Swipeable

In swipeable mode, you can switch tabs with swipe gestrue in the content.

```html
<icloudata-tabs v-model:active="active" swipeable>
  <icloudata-tab v-for="index in 4" :title="'tab ' + index">
    content {{ index }}
  </icloudata-tab>
</icloudata-tabs>
```

### Scrollspy

In scrollspy mode, the list of content will be tiled.

```html
<icloudata-tabs v-model:active="active" scrollspy sticky>
  <icloudata-tab v-for="index in 8" :title="'tab ' + index">
    content {{ index }}
  </icloudata-tab>
</icloudata-tabs>
```

### Before Change

```html
<icloudata-tabs :before-change="beforeChange">
  <icloudata-tab v-for="index in 4" :title="'tab ' + index">
    content {{ index }}
  </icloudata-tab>
</icloudata-tabs>
```

```js
export default {
  setup() {
    const beforeChange = (index) => {
      // prevent change
      if (index === 1) {
        return false;
      }

      // async
      return new Promise((resolve) => {
        resolve(index !== 3);
      });
    };

    return {
      beforeChange,
    };
  },
};
```

## API

### Tabs Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| v-model:active | Index of active tab | _number \| string_ | `0` |
| type | Can be set to `line` `card` | _string_ | `line` |
| color | Tab color | _string_ | `#ee0a24` |
| background | Background color | _string_ | `white` |
| duration | Toggle tab's animation time | _number \| string_ | `0.3` | - |
| line-width | Width of tab line | _number \| string_ | `40px` |
| line-height | Height of tab line | _number \| string_ | `3px` |
| animated | Whether to change tabs with animation | _boolean_ | `false` |
| border | Whether to show border when `type="line"` | _boolean_ | `false` |
| ellipsis | Whether to ellipsis too long title | _boolean_ | `true` |
| sticky | Whether to use sticky mode | _boolean_ | `false` |
| swipeable | Whether to switch tabs with swipe gestrue in the content | _boolean_ | `false` |
| lazy-render | Whether to enable tab content lazy render | _boolean_ | `true` |
| scrollspy `v2.3.0` | Whether to use scrollspy mode | _boolean_ | `false` |
| offset-top `v2.8.7` | Sticky offset top , supports `px` `vw` `vh` `rem` unit, default `px` | _number \| string_ | `0` |
| swipe-threshold | Set swipe tabs threshold | _number \| string_ | `5` | - |
| title-active-color | Title active color | _string_ | - |
| title-inactive-color | Title inactive color | _string_ | - |
| before-change `v2.9.3` | Callback function before changing tabs，return `false` to prevent change，support return Promise | _(name) => boolean \| Promise_ | - |

### Tab Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| title | Title | _string_ | - |
| disabled | Whether to disable tab | _boolean_ | `false` |
| dot `v2.3.0` | Whether to show red dot on the title | _boolean_ | `false` |
| badge `v2.5.6` | Content of the badge on the title | _number \| string_ | - |
| name | Identifier | _number \| string_ | Index of tab |
| url | Link | _string_ | - |
| to | Target route of the link, same as to of vue-router | _string \| object_ | - |
| replace | If true, the navigation will not leave a history record | _boolean_ | `false` |
| title-style | Custom title style | _any_ | - |
| title-class | Custom title class name | _any_ | - |

### Tabs Events

| Event | Description | Arguments |
| --- | --- | --- |
| click | Emitted when a tab is clicked | name，title |
| change | Emitted when active tab changed | name，title |
| disabled | Emitted when a disabled tab is clicked | name，title |
| rendered `v2.3.0` | Emitted when content first rendered in lazy-render mode | name，title |
| scroll | Emitted when tab scrolling in sticky mode | object: { scrollTop, isFixed } |

### Tabs Methods

Use [ref](https://v3.vuejs.org/guide/component-template-refs.html) to get Tabs instance and call instance methods.

| Name | Description | Attribute | Return value |
| --- | --- | --- | --- |
| resize | Resize Tabs when container element resized or visibility changed | - | - |
| scrollTo `v2.9.3` | Go to specified tab in scrollspy mode | name | - |

### Tabs Slots

| Name      | Description              |
| --------- | ------------------------ |
| nav-left  | Custom nav left content  |
| nav-right | Custom nav right content |

### Tab Slots

| Name    | Description      |
| ------- | ---------------- |
| default | Content of tab   |
| title   | Custom tab title |

### Less Variables

How to use: [Custom Theme](#/en-US/theme).

| Name                       | Default Value         | Description |
| -------------------------- | --------------------- | ----------- |
| @tab-text-color            | `@gray-7`             | -           |
| @tab-active-text-color     | `@text-color`         | -           |
| @tab-disabled-text-color   | `@gray-5`             | -           |
| @tab-font-size             | `@font-size-md`       | -           |
| @tab-line-height           | `@line-height-md`     | -           |
| @tabs-default-color        | `@red`                | -           |
| @tabs-line-height          | `44px`                | -           |
| @tabs-card-height          | `30px`                | -           |
| @tabs-nav-background-color | `@white`              | -           |
| @tabs-bottom-bar-width     | `40px`                | -           |
| @tabs-bottom-bar-height    | `3px`                 | -           |
| @tabs-bottom-bar-color     | `@tabs-default-color` | -           |
