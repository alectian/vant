# Form

### Install

```js
import { createApp } from 'vue';
import { Form } from 'cloudata';

const app = createApp();
app.use(Form);
```

## Usage

### Basic Usage

```html
<icloudata-form @submit="onSubmit">
  <icloudata-field
    v-model="state.username"
    name="Username"
    label="Username"
    placeholder="Username"
    :rules="[{ required: true, message: 'Username is required' }]"
  />
  <icloudata-field
    v-model="state.password"
    type="password"
    name="Password"
    label="Password"
    placeholder="Password"
    :rules="[{ required: true, message: 'Password is required' }]"
  />
  <div style="margin: 16px;">
    <icloudata-button round block type="primary" native-type="submit">
      Submit
    </icloudata-button>
  </div>
</icloudata-form>
```

```js
import { reactive } from 'vue';

export default {
  setup() {
    const state = reactive({
      username: '',
      password: '',
    });
    const onSubmit = (values) => {
      console.log('submit', values);
    };

    return {
      state,
      onSubmit,
    };
  },
};
```

### Validate Rules

```html
<icloudata-form validate-first @failed="onFailed">
  <icloudata-field
    v-model="state.value1"
    name="pattern"
    placeholder="USe pattern"
    :rules="[{ pattern, message: 'Error message' }]"
  />
  <icloudata-field
    v-model="state.value2"
    name="validator"
    placeholder="Use validator"
    :rules="[{ validator, message: 'Error message' }]"
  />
  <icloudata-field
    v-model="state.value3"
    name="asyncValidator"
    placeholder="Use async validator"
    :rules="[{ validator: asyncValidator, message: 'Error message' }]"
  />
  <div style="margin: 16px;">
    <icloudata-button round block type="primary" native-type="submit">
      Submit
    </icloudata-button>
  </div>
</icloudata-form>
```

```js
import { reactive } from 'vue';
import { Toast } from 'cloudata';

export default {
  setup() {
    const state = reactive({
      value1: '',
      value2: '',
      value3: '',
    });
    const pattern = /\d{6}/;

    const validator = (val) => /1\d{10}/.test(val);

    const asyncValidator = (val) =>
      new Promise((resolve) => {
        Toast.loading('Validating...');

        setTimeout(() => {
          Toast.clear();
          resolve(/\d{6}/.test(val));
        }, 1000);
      });

    const onFailed = (errorInfo) => {
      console.log('failed', errorInfo);
    };

    return {
      state,
      pattern,
      onFailed,
      validator,
      asyncValidator,
    };
  },
};
```

### Field Type - Switch

```html
<icloudata-field name="switch" label="Switch">
  <template #input>
    <icloudata-switch v-model="checked" size="20" />
  </template>
</icloudata-field>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const checked = ref(false);
    return { checked };
  },
};
```

### Field Type - Checkbox

```html
<icloudata-field name="checkbox" label="Checkbox">
  <template #input>
    <icloudata-checkbox v-model="checked" shape="square" />
  </template>
</icloudata-field>
<icloudata-field name="checkboxGroup" label="CheckboxGroup">
  <template #input>
    <icloudata-checkbox-group v-model="groupChecked" direction="horizontal">
      <icloudata-checkbox name="1" shape="square">Checkbox 1</icloudata-checkbox>
      <icloudata-checkbox name="2" shape="square">Checkbox 2</icloudata-checkbox>
    </icloudata-checkbox-group>
  </template>
</icloudata-field>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const checked = ref(false);
    const groupChecked = ref([]);
    return {
      checked,
      groupChecked,
    };
  },
};
```

### Field Type - Radio

```html
<icloudata-field name="radio" label="Radio">
  <template #input>
    <icloudata-radio-group v-model="checked" direction="horizontal">
      <icloudata-radio name="1">Radio 1</icloudata-radio>
      <icloudata-radio name="2">Radio 2</icloudata-radio>
    </icloudata-radio-group>
  </template>
</icloudata-field>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const checked = ref('1');
    return { checked };
  },
};
```

### Field Type - Stepper

```html
<icloudata-field name="stepper" label="Stepper">
  <template #input>
    <icloudata-stepper v-model="value" />
  </template>
</icloudata-field>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const value = ref(1);
    return { value };
  },
};
```

### Field Type - Rate

```html
<icloudata-field name="rate" label="Rate">
  <template #input>
    <icloudata-rate v-model="value" />
  </template>
</icloudata-field>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const value = ref(3);
    return { value };
  },
};
```

### Field Type - Slider

```html
<icloudata-field name="slider" label="Slider">
  <template #input>
    <icloudata-slider v-model="value" />
  </template>
</icloudata-field>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const value = ref(50);
    return { value };
  },
};
```

### Field Type - Uploader

```html
<icloudata-field name="uploader" label="Uploader">
  <template #input>
    <icloudata-uploader v-model="value" />
  </template>
</icloudata-field>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const value = ref([{ url: 'https://img.yzcdn.cn/vant/leaf.jpg' }]);
    return { value };
  },
};
```

### Field Type - Picker

```html
<icloudata-field
  readonly
  clickable
  name="picker"
  :value="state.value"
  label="Picker"
  placeholder="Select city"
  @click="state.showPicker = true"
/>
<icloudata-popup v-model:show="state.showPicker" position="bottom">
  <icloudata-picker
    :columns="columns"
    @confirm="onConfirm"
    @cancel="state.showPicker = false"
  />
</icloudata-popup>
```

```js
import { reactive } from 'vue';

export default {
  setup() {
    const state = reactive({
      value: '',
      showPicker: false,
    });
    const columns = ['Delaware', 'Florida', 'Georqia', 'Indiana', 'Maine'];

    const onConfirm = (value) => {
      state.value = value;
      state.showPicker = false;
    };

    return {
      state,
      columns,
      onConfirm,
    };
  },
};
```

### Field Type - DatetimePicker

```html
<icloudata-field
  readonly
  clickable
  name="datetimePicker"
  :value="state.value"
  label="Datetime Picker"
  placeholder="Select time"
  @click="state.showPicker = true"
/>
<icloudata-popup v-model:show="state.showPicker" position="bottom">
  <icloudata-datetime-picker
    type="time"
    @confirm="onConfirm"
    @cancel="state.showPicker = false"
  />
</icloudata-popup>
```

```js
import { reactive } from 'vue';

export default {
  setup() {
    const state = reactive({
      value: '',
      showPicker: false,
    });
    const onConfirm = (value) => {
      state.value = value;
      state.showPicker = false;
    };

    return {
      state,
      onConfirm,
    };
  },
};
```

### Field Type - Area

```html
<icloudata-field
  readonly
  clickable
  name="area"
  :value="state.value"
  label="Area Picker"
  placeholder="Select area"
  @click="state.showArea = true"
/>
<icloudata-popup v-model:show="state.showArea" position="bottom">
  <icloudata-area
    :area-list="areaList"
    @confirm="onConfirm"
    @cancel="state.showArea = false"
  />
</icloudata-popup>
```

```js
import { reactive } from 'vue';

export default {
  setup() {
    const state = reactive({
      value: '',
      showArea: false,
    });
    const onConfirm = (value) => {
      state.showArea = false;
      state.value = values
        .filter((item) => !!item)
        .map((item) => item.name)
        .join('/');
    };

    return {
      state,
      areaList: {},
      onConfirm,
    };
  },
};
```

### Field Type - Calendar

```html
<icloudata-field
  readonly
  clickable
  name="calendar"
  :value="state.value"
  label="Calendar"
  placeholder="Select date"
  @click="state.showCalendar = true"
/>
<icloudata-calendar v-model="state.showCalendar" @confirm="onConfirm" />
```

```js
import { reactive } from 'vue';

export default {
  setup() {
    const state = reactive({
      value: '',
      showCalendar: false,
    });
    const onConfirm = (date) => {
      state.value = `${date.getMonth() + 1}/${date.getDate()}`;
      state.showCalendar = false;
    };

    return {
      state,
      onConfirm,
    };
  },
};
```

## API

### Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| label-width | Field label width | _number \| string_ | `6.2em` |
| label-align | Field label align, can be set to `center` `right` | _string_ | `left` |
| input-align | Field input align, can be set to `center` `right` | _string_ | `left` |
| error-message-align | Error message align, can be set to `center` `right` | _string_ | `left` |
| validate-trigger `v2.5.2` | When to validate the form，can be set to `onChange`、`onSubmit` | _string_ | `onBlur` |
| colon | Whether to display colon after label | _boolean_ | `false` |
| validate-first | Whether to stop the validation when a rule fails | _boolean_ | `false` |
| scroll-to-error `v2.5.2` | Whether to scroll to the error field when validation failed | _boolean_ | `false` |
| show-error `v2.6.0` | Whether to highlight input when validation failed | _boolean_ | `true` |
| show-error-message `v2.5.8` | Whether to show error message when validation failed | _boolean_ | `true` |
| submit-on-enter `v2.8.3` | Whether to submit form on enter | _boolean_ | `true` |

### Data Structure of Rule

| Key | Description | Type |
| --- | --- | --- |
| required | Whether to be a required field | _boolean_ |
| message `v2.5.3` | Error message | _string \| (value, rule) => string_ |
| validator `v2.5.3` | Custom validator | _(value, rule) => boolean \| Promise_ |
| pattern `v2.5.3` | Regex pattern | _RegExp_ |
| trigger `v2.5.2` | When to validate the form，can be set to `onChange`、`onBlur` | _string_ |
| formatter `v2.5.3` | Format value before validate | _(value, rule) => any_ |

### validate-trigger

| Value    | Description                                                     |
| -------- | --------------------------------------------------------------- |
| onSubmit | Trigger validation after submiting form                         |
| onBlur   | Trigger validation after submiting form or bluring input        |
| onChange | Trigger validation after submiting form or changing input value |

### Events

| Event | Description | Arguments |
| --- | --- | --- |
| submit | Emitted after submitting the form and validation passed | _values: object_ |
| failed | Emitted after submitting the form and validation failed | _errorInfo: { values: object, errors: object[] }_ |

### Methods

Use [ref](https://v3.vuejs.org/guide/component-template-refs.html) to get Form instance and call instance methods.

| Name | Description | Attribute | Return value |
| --- | --- | --- | --- |
| submit | Submit form | - | - |
| validate | Validate form | _name?: string_ | _Promise_ |
| resetValidation | Reset validation | _name?: string_ | - |
| scrollToField `v2.8.3` | Scroll to field | _name: string, alignToTop: boolean_ | - |

### Slots

| Name    | Description  |
| ------- | ------------ |
| default | Form content |
