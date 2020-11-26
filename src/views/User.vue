<template>
  <div>
    {{ $route.params.id }}:user
    <div>
      <router-link
        :to="{ name: 'UserProfile', params: { id: $route.params.id } }"
        >profile</router-link
      >
    </div>
    <div>
      <router-view></router-view>
    </div>
  </div>
</template>
<script>
export default {
  watch: {
    $route(to, from) {
      console.log("route changed", to, from);
    }
  },
  computed: {}
};
</script>
