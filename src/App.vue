<template>
  <div id="app">
    <img src="./assets/logo.png">
    <div>
      <button @click="startHacking">Start</button>
      <Drawer ref="drawer" :visible.sync="visible" :before-close="handleClose"></Drawer>
    </div>
  </div>
</template>

<script>
import Drawer from './Component/Drawer';
export default {
  name: "App",
  data () {
    return {
      direction: 'direction',
      customClass: 'customClass',
      visible: true,
      demo: true
    };
  },
  components: {
    Drawer
  },
  methods: {
    startHacking() {
      console.log('startHacking');
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
