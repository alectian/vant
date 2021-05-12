# Tabbar

### Install

```js
import { createApp } from 'vue';
import { Tabbar, TabbarItem } from 'cloudata';

const app = createApp();
app.use(Tabbar);
app.use(TabbarItem);
```

## Usage

### Basic Usage

```html
<icloudata-tabbar v-model="active">
  <icloudata-tabbar-item icon="home-o">Tab</icloudata-tabbar-item>
  <icloudata-tabbar-item icon="search">Tab</icloudata-tabbar-item>
  <icloudata-tabbar-item icon="friends-o">Tab</icloudata-tabbar-item>
  <icloudata-tabbar-item icon="setting-o">Tab</icloudata-tabbar-item>
</icloudata-tabbar>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const active = ref(0);
    return { active };
  },
};
```

### Match by name

```html
<icloudata-tabbar v-model="active">
  <icloudata-tabbar-item name="home" icon="home-o">Tab</icloudata-tabbar-item>
  <icloudata-tabbar-item name="search" icon="search">Tab</icloudata-tabbar-item>
  <icloudata-tabbar-item name="friends" icon="friends-o">Tab</icloudata-tabbar-item>
  <icloudata-tabbar-item name="setting" icon="setting-o">Tab</icloudata-tabbar-item>
</icloudata-tabbar>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const active = ref('home');
    return { active };
  },
};
```

### Show Badge

```html
<icloudata-tabbar v-model="active">
  <icloudata-tabbar-item icon="home-o">Tab</icloudata-tabbar-item>
  <icloudata-tabbar-item icon="search" dot>Tab</icloudata-tabbar-item>
  <icloudata-tabbar-item icon="friends-o" badge="5">Tab</icloudata-tabbar-item>
  <icloudata-tabbar-item icon="setting-o" badge="20">Tab</icloudata-tabbar-item>
</icloudata-tabbar>
```

### Custom Icon

Use `icon` slot to custom icon.

```html
<icloudata-tabbar v-model="active">
  <icloudata-tabbar-item badge="3">
    <span>Custom</span>
    <template #icon="props">
      <img :src="props.active ? icon.active : icon.inactive" />
    </template>
  </icloudata-tabbar-item>
  <icloudata-tabbar-item icon="search">Tab</icloudata-tabbar-item>
  <icloudata-tabbar-item icon="setting-o">Tab</icloudata-tabbar-item>
</icloudata-tabbar>
```

```js
import { ref } from 'vue';

export default {
  setup() {
    const active = ref(0);
    const icon = {
      active: 'https://img.yzcdn.cn/vant/user-active.png',
      inactive: 'https://img.yzcdn.cn/vant/user-inactive.png',
    };
    return {
      icon,
      active,
    };
  },
};
```

### Custom Color

```html
<icloudata-tabbar v-model="active" active-color="#ee0a24" inactive-color="#000">
  <icloudata-tabbar-item icon="home-o">Tab</icloudata-tabbar-item>
  <icloudata-tabbar-item icon="search">Tab</icloudata-tabbar-item>
  <icloudata-tabbar-item icon="friends-o">Tab</icloudata-tabbar-item>
  <icloudata-tabbar-item icon="setting-o">Tab</icloudata-tabbar-item>
</icloudata-tabbar>
```

### Change Event

```html
<icloudata-tabbar v-model="active" @change="onChange">
  <icloudata-tabbar-item icon="home-o">Tab 1</icloudata-tabbar-item>
  <icloudata-tabbar-item icon="search">Tab 2</icloudata-tabbar-item>
  <icloudata-tabbar-item icon="friends-o">Tab 3</icloudata-tabbar-item>
  <icloudata-tabbar-item icon="setting-o">Tab 4</icloudata-tabbar-item>
</icloudata-tabbar>
```

```js
import { ref } from 'vue';
import { Toast } from 'cloudata';

export default {
  setup() {
    const active = ref(0);
    const onChange = (index) => {
      Toast(`Tab ${index}`);
    };

    return {
      icon,
      onChange,
    };
  },
};
```

### Route Mode

```html
<router-view />

<icloudata-tabbar route>
  <icloudata-tabbar-item replace to="/home" icon="home-o">Tab</icloudata-tabbar-item>
  <icloudata-tabbar-item replace to="/search" icon="search">Tab</icloudata-tabbar-item>
</icloudata-tabbar>
```

## API

### Tabbar Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| v-model | Identifier of current tab | _number \| string_ | `0` |
| fixed | Whether to fixed bottom | _boolean_ | `true` |
| border | Whether to show border | _boolean_ | `true` |
| z-index | Z-index | _number \| string_ | `1` |
| active-color | Color of active tab item | _string_ | `#1989fa` |
| inactive-color | Color of inactive tab item | _string_ | `#7d7e80` |
| route | Whether to enable route mode | _boolean_ | `false` |
| placeholder `v2.6.0` | Whether to generage a placeholder element when fixed | _boolean_ | `false` |
| safe-area-inset-bottom | Whether to enable bottom safe area adaptation | _boolean_ | `false` |
| before-change `v2.10.4` | Callback function before changing tabs，return `false` to prevent change，support return Promise | _(name) => boolean \| Promise_ | - |

### Tabbar Events

| Event  | Description                      | Arguments                    |
| ------ | -------------------------------- | ---------------------------- |
| change | Emitted when changing active tab | active: index of current tab |

### TabbarItem Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| name | Identifier | _number \| string_ | Item index |
| icon | Icon name | _string_ | - |
| icon-prefix `v2.5.3` | Icon className prefix | _string_ | `van-icon` |
| dot | Whether to show red dot | _boolean_ | - |
| badge `v2.5.6` | Content of the badge | _number \| string_ | `''` |
| url | Link | _string_ | - |
| to | Target route of the link, same as to of vue-router | _string \| object_ | - |
| replace | If true, the navigation will not leave a history record | _boolean_ | `false` |

### TabbarItem Slots

| Name | Description | SlotProps |
| ---- | ----------- | --------- |
| icon | Custom icon | active    |

### Less Variables

How to use: [Custom Theme](#/en-US/theme).

| Name | Default Value | Description |
| --- | --- | --- |
| @tabbar-height | `50px` | - |
| @tabbar-z-index | `1` | - |
| @tabbar-background-color | `@white` | - |
| @tabbar-item-font-size | `@font-size-sm` | - |
| @tabbar-item-text-color | `@gray-7` | - |
| @tabbar-item-active-color | `@blue` | - |
| @tabbar-item-active-background-color | `@tabbar-background-color` | - |
| @tabbar-item-line-height | `1` | - |
| @tabbar-item-icon-size | `22px` | - |
| @tabbar-item-margin-bottom | `4px` | - |
