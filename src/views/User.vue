<template>
  <div>{{ $route.params.id }}:user</div>
</template>
<script>
export default {
  watch: {
    $route(to, from) {
      console.log("route changed", to, from);
    }
  }
};
</script>
