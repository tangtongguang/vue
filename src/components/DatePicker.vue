<template>
  <div>
    <select v-bind="$attrs">
      <option>A</option>
      <option>B</option>
    </select>
  </div>
</template>
<script>
export default {
  inheritAttrs: false
};
</script>
