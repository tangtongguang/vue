<template>
  <div><input v-model="value" type="text" />{{ value }}</div>
</template>
<script>
export default {
  props: {
    modelValue: {
      type: String,
      default: ""
    }
  },
  computed: {
    value: {
      get() {
        return this.modelValue;
      },
      set(value) {
        this.$emit("update:modelValue", value);
      }
    }
  }
};
</script>
