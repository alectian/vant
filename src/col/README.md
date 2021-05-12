# Layout

### Intro

Quickly and easily create layouts with `icloudata-row` and `icloudata-col`.

### Install

```js
import { createApp } from 'vue';
import { Col, Row } from 'cloudata';

const app = createApp();
app.use(Col);
app.use(Row);
```

## Usage

### Basic Usage

Layout are based on 24-column. The attribute `span` in `Col` means the number of column the grid spans. Of course, You can use `offset` attribute to set number of spacing on the left side of the grid.

```html
<icloudata-row>
  <icloudata-col span="8">span: 8</icloudata-col>
  <icloudata-col span="8">span: 8</icloudata-col>
  <icloudata-col span="8">span: 8</icloudata-col>
</icloudata-row>

<icloudata-row>
  <icloudata-col span="4">span: 4</icloudata-col>
  <icloudata-col span="10" offset="4">offset: 4, span: 10</icloudata-col>
  <icloudata-col span="6">span: 6</icloudata-col>
</icloudata-row>

<icloudata-row>
  <icloudata-col offset="12" span="12">offset: 12, span: 12</icloudata-col>
</icloudata-row>
```

### Column Spacing

Set grid spacing using `gutter` attribute. The default value is 0.

```html
<icloudata-row gutter="20">
  <icloudata-col span="8">span: 8</icloudata-col>
  <icloudata-col span="8">span: 8</icloudata-col>
  <icloudata-col span="8">span: 8</icloudata-col>
</icloudata-row>
```

### Justify Content

```html
<icloudata-row justify="center">
  <icloudata-col span="6">span: 6</icloudata-col>
  <icloudata-col span="6">span: 6</icloudata-col>
  <icloudata-col span="6">span: 6</icloudata-col>
</icloudata-row>

<icloudata-row justify="end">
  <icloudata-col span="6">span: 6</icloudata-col>
  <icloudata-col span="6">span: 6</icloudata-col>
  <icloudata-col span="6">span: 6</icloudata-col>
</icloudata-row>

<icloudata-row justify="space-between">
  <icloudata-col span="6">span: 6</icloudata-col>
  <icloudata-col span="6">span: 6</icloudata-col>
  <icloudata-col span="6">span: 6</icloudata-col>
</icloudata-row>

<icloudata-row justify="space-around">
  <icloudata-col span="6">span: 6</icloudata-col>
  <icloudata-col span="6">span: 6</icloudata-col>
  <icloudata-col span="6">span: 6</icloudata-col>
</icloudata-row>
```

## API

### Row Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| gutter | Grid spacing（px） | _number \| string_ | - |
| tag | Custom element tag | _string_ | `div` |
| justify | Flex main axis，can be set to end/center/space-around/space-between | _string_ | `start` |
| align | Flex cross axis, be set to center/bottom | _string_ | `top` |

### Col Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| span | number of column the grid spans | _number \| string_ | - |
| offset | number of spacing on the left side of the grid | _number \| string_ | - |
| tag | Custom element tag | _string_ | `div` |

### Row Events

| Event | Description                     | Arguments      |
| ----- | ------------------------------- | -------------- |
| click | Emitted when the row is clicked | _event: Event_ |

### Col Events

| Event | Description                     | Arguments      |
| ----- | ------------------------------- | -------------- |
| click | Emitted when the col is clicked | _event: Event_ |
