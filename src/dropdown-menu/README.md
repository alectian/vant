# DropdownMenu

### Install

```js
import { createApp } from 'vue';
import { DropdownMenu, DropdownItem } from 'cloudata';

const app = createApp();
app.use(DropdownMenu);
app.use(DropdownItem);
```

## Usage

### Basic Usage

```html
<icloudata-dropdown-menu>
  <icloudata-dropdown-item v-model="state.value1" :options="option1" />
  <icloudata-dropdown-item v-model="state.value2" :options="option2" />
</icloudata-dropdown-menu>
```

```js
import { reactive } from 'vue';

export default {
  setup() {
    const state = reactive({
      value1: 0,
      value2: 'a',
    });
    const option1 = [
      { text: 'Option1', value: 0 },
      { text: 'Option2', value: 1 },
      { text: 'Option3', value: 2 },
    ];
    const option2 = [
      { text: 'Option A', value: 'a' },
      { text: 'Option B', value: 'b' },
      { text: 'Option C', value: 'c' },
    ];

    return {
      state,
      option1,
      option2,
    };
  },
};
```

### Custom Content

```html
<icloudata-dropdown-menu>
  <icloudata-dropdown-item v-model="state.value" :options="option" />
  <icloudata-dropdown-item title="Title" ref="item">
    <icloudata-cell center title="Title">
      <template #right-icon>
        <icloudata-switch v-model="state.switch1" size="24" active-color="#ee0a24" />
      </template>
    </icloudata-cell>
    <icloudata-cell center title="Title">
      <template #right-icon>
        <icloudata-switch v-model="state.switch2" size="24" active-color="#ee0a24" />
      </template>
    </icloudata-cell>
    <div style="padding: 5px 16px;">
      <icloudata-button type="danger" block round @click="onConfirm">
        Confirm
      </icloudata-button>
    </div>
  </icloudata-dropdown-item>
</icloudata-dropdown-menu>
```

```js
import { ref, reactive } from 'vue';

export default {
  setup() {
    const item = ref(null);
    const state = reactive({
      value: 0,
      switch1: false,
      switch2: false,
    });
    const options = [
      { text: 'Option1', value: 0 },
      { text: 'Option2', value: 1 },
      { text: 'Option3', value: 2 },
    ];
    const onConfirm = () => {
      item.value.toggle();
    };

    return {
      item,
      state,
      option,
      onConfirm,
    };
  },
};
```

### Custom Active Color

Use `active-color` prop to custom active color of the title and options.

```html
<icloudata-dropdown-menu active-color="#1989fa">
  <icloudata-dropdown-item v-model="value1" :options="option1" />
  <icloudata-dropdown-item v-model="value2" :options="option2" />
</icloudata-dropdown-menu>
```

### Expand Direction

```html
<icloudata-dropdown-menu direction="up">
  <icloudata-dropdown-item v-model="value1" :options="option1" />
  <icloudata-dropdown-item v-model="value2" :options="option2" />
</icloudata-dropdown-menu>
```

### Disabled

```html
<icloudata-dropdown-menu>
  <icloudata-dropdown-item v-model="value1" disabled :options="option1" />
  <icloudata-dropdown-item v-model="value2" disabled :options="option2" />
</icloudata-dropdown-menu>
```

## API

### DropdownMenu Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| active-color | Active color of title and option | _string_ | `#ee0a24` |
| direction | Expand direction, can be set to `up` | _string_ | `down` |
| z-index | z-index of menu item | _number \| string_ | `10` |
| duration | Transition duration, unit second | _number \| string_ | `0.2` |
| overlay | Whether to show overlay | _boolean_ | `true` |
| close-on-click-overlay | Whether to close when overlay is clicked | _boolean_ | `true` |
| close-on-click-outside | Whether to close when outside is clicked | _boolean_ | `true` |

### DropdownItem Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| value | Value of current option，can use `v-model` | _number \| string_ | - |
| title | Item title | _string_ | Text of selected option |
| options | Options | _Option[]_ | `[]` |
| disabled | Whether to disable dropdown item | _boolean_ | `false` |
| lazy-render `v2.8.5` | Whether to lazy render util opened | _boolean_ | `true` |
| title-class | Title class | _string_ | - |
| teleport | Return the mount node for menu | _string \| Element_ | - |

### DropdownItem Events

| Event  | Description                             | Arguments |
| ------ | --------------------------------------- | --------- |
| change | Emitted select option and value changed | value     |
| open   | Emitted when opening menu               | -         |
| close  | Emitted when closing menu               | -         |
| opened | Emitted when menu is opened             | -         |
| closed | Emitted when menu is closed             | -         |

### DropdownItem Slots

| Name    | Description  |
| ------- | ------------ |
| default | Content      |
| title   | Custom title |

### DropdownItem Methods

Use [ref](https://v3.vuejs.org/guide/component-template-refs.html) to get DropdownItem instance and call instance methods.

| Name   | Description    | Attribute       | Return value |
| ------ | -------------- | --------------- | ------------ |
| toggle | Toggle display | _show: boolean_ | -            |

### Data Structure of Option

| Key   | Description | Type               |
| ----- | ----------- | ------------------ |
| text  | Text        | _string_           |
| value | Value       | _number \| string_ |
| icon  | Left icon   | _string_           |

### Less Variables

How to use: [Custom Theme](#/en-US/theme).

| Name | Default Value | Description |
| --- | --- | --- |
| @dropdown-menu-height | `48px` | - |
| @dropdown-menu-background-color | `@white` | - |
| @dropdown-menu-box-shadow | `0 2px 12px fade(@gray-7, 12)` | - |
| @dropdown-menu-title-font-size | `15px` | - |
| @dropdown-menu-title-text-color | `@text-color` | - |
| @dropdown-menu-title-active-text-color | `@red` | - |
| @dropdown-menu-title-disabled-text-color | `@gray-6` | - |
| @dropdown-menu-title-padding | `0 @padding-xs` | - |
| @dropdown-menu-title-line-height | `@line-height-lg` | - |
| @dropdown-menu-option-active-color | `@red` | - |
| @dropdown-menu-content-max-height | `80%` | - |
| @dropdown-item-z-index | `10` | - |
