# Checkbox

### Install

```js
import { createApp } from 'vue';
import { Checkbox, CheckboxGroup } from 'cloudata';

const app = createApp();
app.use(Checkbox);
app.use(CheckboxGroup);
```

## Usage

### Basic Usage

```html
<icloudata-checkbox v-model="checked">Checkbox</icloudata-checkbox>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const checked = ref(true);
    return {
      checked,
    };
  },
};
```

### Disabled

```html
<icloudata-checkbox v-model="checked" disabled>Checkbox</icloudata-checkbox>
```

### Custom Shape

```html
<icloudata-checkbox v-model="checked" shape="square">Checkbox</icloudata-checkbox>
```

### Custom Color

```html
<icloudata-checkbox v-model="checked" checked-color="#ee0a24">Checkbox</icloudata-checkbox>
```

### Custom Icon Size

```html
<icloudata-checkbox v-model="checked" icon-size="24px">Checkbox</icloudata-checkbox>
```

### Custom Icon

Use icon slot to custom icon.

```html
<icloudata-checkbox v-model="checked">
  customize icon
  <template #icon="props">
    <img class="img-icon" :src="props.checked ? activeIcon : inactiveIcon" />
  </template>
</icloudata-checkbox>

<style>
  .img-icon {
    height: 20px;
  }
</style>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const checked = ref(true);
    return {
      checked,
      activeIcon: 'https://img.yzcdn.cn/vant/user-active.png',
      inactiveIcon: 'https://img.yzcdn.cn/vant/user-inactive.png',
    };
  },
};
```

### Disable Label Click

```html
<icloudata-checkbox v-model="checked" label-disabled>Checkbox</icloudata-checkbox>
```

### Checkbox Group

When Checkboxes are inside a CheckboxGroup, the checked checkboxes's name is an array and bound with CheckboxGroup by v-model.

```html
<icloudata-checkbox-group v-model="checked">
  <icloudata-checkbox name="a">Checkbox a</icloudata-checkbox>
  <icloudata-checkbox name="b">Checkbox b</icloudata-checkbox>
</icloudata-checkbox-group>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const checked = ref(['a', 'b']);
    return { checked };
  },
};
```

### Horizontal

```html
<icloudata-checkbox-group v-model="checked" direction="horizontal">
  <icloudata-checkbox name="a">Checkbox a</icloudata-checkbox>
  <icloudata-checkbox name="b">Checkbox b</icloudata-checkbox>
</icloudata-checkbox-group>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const checked = ref([]);
    return { checked };
  },
};
```

### Maximum amount of checked options

```html
<icloudata-checkbox-group v-model="result" :max="2">
  <icloudata-checkbox name="a">Checkbox a</icloudata-checkbox>
  <icloudata-checkbox name="b">Checkbox b</icloudata-checkbox>
  <icloudata-checkbox name="c">Checkbox c</icloudata-checkbox>
</icloudata-checkbox-group>
```

### Toggle All

```html
<icloudata-checkbox-group v-model="checked" ref="checkboxGroup">
  <icloudata-checkbox name="a">Checkbox a</icloudata-checkbox>
  <icloudata-checkbox name="b">Checkbox b</icloudata-checkbox>
  <icloudata-checkbox name="c">Checkbox c</icloudata-checkbox>
</icloudata-checkbox-group>

<icloudata-button type="primary" @click="checkAll">Check All</icloudata-button>
<icloudata-button type="primary" @click="toggleAll">Toggle All</icloudata-button>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const checked = ref([]);
    const checkboxGroup = ref(null);

    const checkAll = () => {
      checkboxGroup.value.toggleAll(true);
    }
    const toggleAll = () => {
      checkboxGroup.value.toggleAll();
    },

    return {
      checked,
      checkAll,
      toggleAll,
      checkboxGroup,
    };
  },
};
```

### Inside a Cell

```html
<icloudata-checkbox-group v-model="checked">
  <icloudata-cell-group>
    <icloudata-cell
      v-for="(item, index) in list"
      clickable
      :key="item"
      :title="`Checkbox ${item}`"
      @click="toggle(index)"
    >
      <template #right-icon>
        <icloudata-checkbox
          :name="item"
          :ref="el => checkboxRefs[index] = el"
          @click.stop
        />
      </template>
    </icloudata-cell>
  </icloudata-cell-group>
</icloudata-checkbox-group>
```

```js
import { ref, onBeforeUpdate } from 'vue';

export default {
  setup() {
    const checked = ref([]);
    const checkboxRefs = ref([]);
    const toggle = (index) => {
      checkboxRefs.value[index].toggle();
    };

    onBeforeUpdate(() => {
      checkboxRefs.value = [];
    });

    return {
      list: ['a', 'b'],
      toggle,
      checked,
      checkboxRefs,
    };
  },
};
```

## API

### Checkbox Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| v-model | Check status | _boolean_ | `false` |
| name | Checkbox name | _any_ | - |
| shape | Can be set to `square` | _string_ | `round` |
| disabled | Disable checkbox | _boolean_ | `false` |
| label-disabled | Whether to disable label click | _boolean_ | `false` |
| label-position | Can be set to `left` | _string_ | `right` |
| icon-size | Icon size | _number \| string_ | `20px` |
| checked-color | Checked color | _string_ | `#1989fa` | - |
| bind-group | Whether to bind with CheckboxGroup | _boolean_ | `true` |

### CheckboxGroup Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| v-model | Names of all checked checkboxes | _any[]_ | - |
| disabled | Whether to disable all checkboxes | _boolean_ | `false` |
| max | Maximum amount of checked options | _number \| string_ | `0`(Unlimited) |
| direction `v2.5.0` | Direction, can be set to `horizontal` | _string_ | `vertical` |
| icon-size | Icon size of all checkboxes | _number \| string_ | `20px` |
| checked-color | Checked color of all checkboxes | _string_ | `#1989fa` | - |

### Checkbox Events

| Event  | Description                          | Parameters         |
| ------ | ------------------------------------ | ------------------ |
| change | Emitted when value changed           | _checked: boolean_ |
| click  | Emitted when the checkbox is clicked | _event: Event_     |

### CheckboxGroup Events

| Event  | Description                | Parameters     |
| ------ | -------------------------- | -------------- |
| change | Emitted when value changed | _names: any[]_ |

### Checkbox Slots

| Name    | Description  | SlotProps          |
| ------- | ------------ | ------------------ |
| default | Custom label | -                  |
| icon    | Custom icon  | _checked: boolean_ |

### CheckboxGroup Methods

Use [ref](https://v3.vuejs.org/guide/component-template-refs.html) to get CheckboxGroup instance and call instance methods.

| Name | Description | Attribute | Return value |
| --- | --- | --- | --- |
| toggleAll | Toggle check status of all checkboxes | _options?: boolean \| object_ | - |

### toggleAll Usage

```js
const { checkboxGroup } = this.$refs;

// Toggle all
checkboxGroup.toggleAll();
// Select all
checkboxGroup.toggleAll(true);
// Unselect all
checkboxGroup.toggleAll(false);

// Toggle all, skip disabled
checkboxGroup.toggleAll({
  skipDisabled: true,
});
// Select all, skip disabled
checkboxGroup.toggleAll({
  checked: true,
  skipDisabled: true,
});
```

### Checkbox Methods

Use [ref](https://v3.vuejs.org/guide/component-template-refs.html) to get Checkbox instance and call instance methods.

| Name   | Description         | Attribute           | Return value |
| ------ | ------------------- | ------------------- | ------------ |
| toggle | Toggle check status | _checked?: boolean_ | -            |

### Less Variables

How to use: [Custom Theme](#/en-US/theme).

| Name | Default Value | Description |
| --- | --- | --- |
| @checkbox-size | `20px` | - |
| @checkbox-border-color | `@gray-5` | - |
| @checkbox-transition-duration | `@animation-duration-fast` | - |
| @checkbox-label-margin | `@padding-xs` | - |
| @checkbox-label-color | `@text-color` | - |
| @checkbox-checked-icon-color | `@blue` | - |
| @checkbox-disabled-icon-color | `@gray-5` | - |
| @checkbox-disabled-label-color | `@gray-5` | - |
| @checkbox-disabled-background-color | `@border-color` | - |
