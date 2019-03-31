<template>
  <div class="item" id={item.id}>
    <img :src="processImgUrl(item.image)" :alt="item.name"/>
    <div class="item__description">
      <strong>{{ item.title }}</strong>
      <span>{{ item.categoryName }}</span>
    </div>
  </div>
</template>

<script>
import { processImgUrl } from '../statics/scripts/helpers.js';

export default {
  name: 'Item',
  props: ['item'],
  methods: {
    processImgUrl
  },
}
</script>
