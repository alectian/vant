# ContactCard 联系人卡片

### 介绍

以卡片的形式展示联系人信息。

### 引入

```js
import { createApp } from 'vue';
import { ContactCard } from 'cloudata';

const app = createApp();
app.use(ContactCard);
```

## 代码演示

### 添加联系人

```html
<icloudata-contact-card type="add" @click="onAdd" />
```

```js
import { Toast } from 'cloudata';

export default {
  setup() {
    const onAdd = () => {
      Toast('新增');
    };
    return {
      onAdd,
    };
  },
};
```

### 编辑联系人

```html
<icloudata-contact-card
  type="edit"
  :name="currentContact.name"
  :tel="currentContact.tel"
  @click="onEdit"
/>
```

```js
import { reactive } from 'vue';
import { Toast } from 'cloudata';

export default {
  setup() {
    const currentContact = reactive({
      name: '张三',
      tel: '13000000000',
    });

    const onEdit = () => {
      Toast('edit');
    };

    return {
      onEdit,
      currentContact,
    };
  },
};
```

### 不可编辑

```html
<icloudata-contact-card type="edit" name="张三" tel="13000000000" :editable="false" />
```

## API

### Props

| 参数     | 说明                      | 类型     | 默认值       |
| -------- | ------------------------- | -------- | ------------ |
| type     | 卡片类型，可选值为 `edit` | _string_ | `add`        |
| name     | 联系人姓名                | _string_ | -            |
| tel      | 联系人手机号              | _string_ | -            |
| add-text | 添加时的文案提示          | _string_ | `添加联系人` |

### Events

| 事件名 | 说明       | 回调参数       |
| ------ | ---------- | -------------- |
| click  | 点击时触发 | _event: Event_ |

### 样式变量

组件提供了下列 Less 变量，可用于自定义样式。

| 名称                            | 默认值            | 描述 |
| ------------------------------- | ----------------- | ---- |
| @contact-card-padding           | `@padding-md`     | -    |
| @contact-card-add-icon-size     | `40px`            | -    |
| @contact-card-add-icon-color    | `@blue`           | -    |
| @contact-card-value-line-height | `@line-height-md` | -    |
