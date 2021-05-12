# Collapse

### Install

```js
import { createApp } from 'vue';
import { Collapse, CollapseItem } from 'cloudata';

const app = createApp();
app.use(Collapse);
app.use(CollapseItem);
```

## Usage

### Basic Usage

Use `v-model` to control the name of active panels.

```html
<icloudata-collapse v-model="activeNames">
  <icloudata-collapse-item title="Title1" name="1">Content</icloudata-collapse-item>
  <icloudata-collapse-item title="Title2" name="2">Content</icloudata-collapse-item>
  <icloudata-collapse-item title="Title3" name="3">Content</icloudata-collapse-item>
</icloudata-collapse>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const activeNames = ref(['1']);
    return { activeNames };
  },
};
```

### Accordion

In accordion mode, only one panel can be expanded at the same time.

```html
<icloudata-collapse v-model="activeName" accordion>
  <icloudata-collapse-item title="Title1" name="1">Content</icloudata-collapse-item>
  <icloudata-collapse-item title="Title2" name="2">Content</icloudata-collapse-item>
  <icloudata-collapse-item title="Title3" name="3">Content</icloudata-collapse-item>
</icloudata-collapse>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const activeName = ref('1');
    return { activeName };
  },
};
```

### Disabled

Use the `disabled` prop to disable CollaseItem.

```html
<icloudata-collapse v-model="activeNames">
  <icloudata-collapse-item title="Title1" name="1">Content</icloudata-collapse-item>
  <icloudata-collapse-item title="Title2" name="2" disabled>
    Content
  </icloudata-collapse-item>
  <icloudata-collapse-item title="Title3" name="3" disabled>
    Content
  </icloudata-collapse-item>
</icloudata-collapse>
```

### Custom title

```html
<icloudata-collapse v-model="activeNames">
  <icloudata-collapse-item name="1">
    <template #title>
      <div>Title1 <icloudata-icon name="question-o" /></div>
    </template>
    Content
  </icloudata-collapse-item>
  <icloudata-collapse-item title="Title2" name="2" icon="shop-o">
    Content
  </icloudata-collapse-item>
</icloudata-collapse>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const activeNames = ref(['1']);
    return { activeNames };
  },
};
```

## API

### Collapse Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| v-model | Names of current active panels | accordion mode： _number \| string_<br>non-accordion mode：_(number \| string)[]_ | - |
| accordion | Whether to be accordion mode | _boolean_ | `false` |
| border | Whether to show outer border | _boolean_ | `true` |

### Collapse Events

| Event  | Description                  | Arguments   |
| ------ | ---------------------------- | ----------- |
| change | Emitted when switching panel | activeNames |

### CollapseItem Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| name | Name | _number \| string_ | `index` |
| icon | Left Icon | _string_ | - |
| size | Title size，can be set to `large` | _string_ | - |
| title | Title | _number \| string_ | - |
| value | Right text | _number \| string_ | - |
| label | Description below the title | _string_ | - |
| border | Whether to show inner border | _boolean_ | `true` |
| disabled | Whether to disabled collapse | _boolean_ | `false` |
| is-link | Whether to show link icon | _boolean_ | `true` |
| title-class | Title className | _string_ | - |
| value-class | Value className | _string_ | - |
| label-class | Label className | _string_ | - |

### CollapseItem Slots

| Name       | Description       |
| ---------- | ----------------- |
| default    | Content           |
| value      | Custom value      |
| icon       | Custom icon       |
| title      | Custom title      |
| right-icon | Custom right icon |

### CollapseItem Methods

Use [ref](https://v3.vuejs.org/guide/component-template-refs.html) to get CollapseItem instance and call instance methods.

| Name | Description | Attribute | Return value |
| --- | --- | --- | --- |
| toggle `v2.10.9` | Toggle expanded status | _expanded: boolean_ | - |

### Less Variables

How to use: [Custom Theme](#/en-US/theme).

| Name | Default Value | Description |
| --- | --- | --- |
| @collapse-item-transition-duration | `@animation-duration-base` | - |
| @collapse-item-content-padding | `@padding-sm @padding-md` | - |
| @collapse-item-content-font-size | `@font-size-md` | - |
| @collapse-item-content-line-height | `1.5` | - |
| @collapse-item-content-text-color | `@gray-6` | - |
| @collapse-item-content-background-color | `@white` | - |
| @collapse-item-title-disabled-color | `@gray-5` | - |
