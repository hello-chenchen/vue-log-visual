<template>
  <div id="app">
    <img src="./assets/logo.png">
    <div>
      <button @click="startHacking">Start</button>
      <log-drawer ref="drawer" :visible.sync="visible" :before-close="handleClose" :log-data="data"></log-drawer>
    </div>
  </div>
</template>

<script>
import LogDrawer from './Component/LogDrawer';
export default {
  name: "App",
  data () {
    return {
      direction: 'direction',
      customClass: 'customClass',
      visible: false,
      demo: true,
      data: []
    };
  },
  components: {
    LogDrawer
  },
  methods: {
    startHacking() {
      let log = {};
      log.type = 'error-message';
      log.message = 'test log';
      this.data.push(log);

      this.visible = true;
    },
    handleClose(done) {
      done();
    }
  }
};
</script>
<style>
#app {
  font-family: Helvetica, sans-serif;
  text-align: center;
}
</style>
