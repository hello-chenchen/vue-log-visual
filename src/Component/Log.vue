<template>
  <div class="log">
    <div v-for="item in logs" :key="item.index" :class="[item.type]">
        <span>{{ item.message }}</span>
    </div>
  </div>
</template>

<script>
export default {
    name: "Log",
    props: {
        logs: {
            type: Array,
            default: []
        }
    }
}
</script>

<style>
.log {
    text-align: left;
    margin: 10px;
}

.error-message {
    color: red;
}

.log-message {
    color: black;
}
</style>