---
tags:
  - vue
  - code
---

refer to stackoverflow post: https://stackoverflow.com/questions/62511252/vuetify-data-table-combine-dynamic-slots-with-row-item-slots

in my case it was for dynamic columns in a v-data-table
```javascript
<template v-for="(slot,i) in creatorSlots" v-slot:[`item.${slot.field}`]="{ item }">
    <strong :key="i">{{item.FIRSTNAME}} {{item.LASTNAME}}</strong>
</template>
```
