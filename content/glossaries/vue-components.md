---
title: "Structure of Vue Components"
publishOn: 2021-12-14T00:00:00
tags: ['Vue','Components']
---
## How are Vue components structured?

A Vue component contains three parts:

- Script block: JavaScript
- Template block: HTML
- Style: CSS

### Example

```js
export default {
  mounted() {
    console.log("It works!");
  }
};
```

```html
<template>
  <h1>My Component Title</h1>
</template>
```