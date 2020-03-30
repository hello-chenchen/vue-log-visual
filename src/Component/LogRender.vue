<template>
  <div class="log">
    <div v-for="item in logs" :key="item.index" :class="[item.type]">
      <span>{{ undefined == item.message ? item : item.message }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Log",
  props: {
    logs: {
      type: Array,
      default: () => {
        return [];
      }
    }
  }
};
</script>

<style>
.error-message {
  color: red;
}

.log-message {
  color: black;
}
</style>