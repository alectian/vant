# Steps

### Install

```js
import { createApp } from 'vue';
import { Step, Steps } from 'cloudata';

const app = createApp();
app.use(Step);
app.use(Steps);
```

## Usage

### Basic Usage

```html
<icloudata-steps :active="active">
  <icloudata-step>Step1</icloudata-step>
  <icloudata-step>Step2</icloudata-step>
  <icloudata-step>Step3</icloudata-step>
  <icloudata-step>Step4</icloudata-step>
</icloudata-steps>
```

```js
import { ref } from 'vue';

export default {
  steup() {
    const active = ref(1);
    return { active };
  },
};
```

### Custom Style

```html
<icloudata-steps :active="active" active-icon="success" active-color="#38f">
  <icloudata-step>Step1</icloudata-step>
  <icloudata-step>Step2</icloudata-step>
  <icloudata-step>Step3</icloudata-step>
  <icloudata-step>Step4</icloudata-step>
</icloudata-steps>
```

### Vertical Steps

```html
<icloudata-steps direction="vertical" :active="0">
  <icloudata-step>
    <h3>【City】Status1</h3>
    <p>2016-07-12 12:40</p>
  </icloudata-step>
  <icloudata-step>
    <h3>【City】Status2</h3>
    <p>2016-07-11 10:00</p>
  </icloudata-step>
  <icloudata-step>
    <h3>【City】Status3</h3>
    <p>2016-07-10 09:30</p>
  </icloudata-step>
</icloudata-steps>
```

## API

### Steps Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| active | Active step | _number \| string_ | `0` |
| direction | Can be set to `vertical` | _string_ | `horizontal` |
| active-color | Active step color | _string_ | `#07c160` |
| inactive-color `v2.9.1` | Inactive step color | _string_ | `#969799` |
| active-icon | Active icon name | _string_ | `checked` |
| inactive-icon | Inactive icon name | _string_ | - |

### Step Slots

| Name          | Description          |
| ------------- | -------------------- |
| active-icon   | Custom active icon   |
| inactive-icon | Custom inactive icon |

### Steps Events

| Event | Description | Arguments |
| --- | --- | --- |
| click-step `v2.5.9` | Emitted when a step's title or icon is clicked | _index: number_ |

### Less Variables

How to use: [Custom Theme](#/en-US/theme).

| Name                             | Default Value   | Description |
| -------------------------------- | --------------- | ----------- |
| @step-text-color                 | `@gray-6`       | -           |
| @step-active-color               | `@green`        | -           |
| @step-process-text-color         | `@text-color`   | -           |
| @step-font-size                  | `@font-size-md` | -           |
| @step-line-color                 | `@border-color` | -           |
| @step-finish-line-color          | `@green`        | -           |
| @step-finish-text-color          | `@text-color`   | -           |
| @step-icon-size                  | `12px`          | -           |
| @step-circle-size                | `5px`           | -           |
| @step-circle-color               | `@gray-6`       | -           |
| @step-horizontal-title-font-size | `@font-size-sm` | -           |
| @steps-background-color          | `@white`        | -           |
