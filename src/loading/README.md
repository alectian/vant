# Loading

### Install

```js
import { createApp } from 'vue';
import { Loading } from 'hello';

const app = createApp();
app.use(Loading);
```

## Usage

### Type

```html
<hello-loading />

<hello-loading type="spinner" />
```

### Color

```html
<hello-loading color="#1989fa" />

<hello-loading type="spinner" color="#1989fa" />
```

### Size

```html
<hello-loading size="24" />

<hello-loading type="spinner" size="24px" />
```

### Text

```html
<hello-loading size="24px">Loading...</van-loading>
```

### Vertical

```html
<hello-loading size="24px" vertical>Loading...</van-loading>
```

## API

### Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| color | Loading color | _string_ | `#c9c9c9` |
| type | Can be set to `spinner` | _string_ | `circular` |
| size | Icon size | _number \| string_ | `30px` |
| text-size | Text font size | _number \| string_ | `14px` |
| vertical | Whether to arrange icons and text content vertically | _boolean_ | `false` |

### Slots

| Name    | Description  |
| ------- | ------------ |
| default | Loading text |

### Less Variables

How to use: [Custom Theme](#/en-US/theme).

| Name                                | Default Value   | Description |
| ----------------------------------- | --------------- | ----------- |
| @loading-text-color                 | `@gray-6`       | -           |
| @loading-text-font-size             | `@font-size-md` | -           |
| @loading-spinner-color              | `@gray-5`       | -           |
| @loading-spinner-size               | `30px`          | -           |
| @loading-spinner-animation-duration | `0.8s`          | -           |
