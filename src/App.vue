<template>
  <div id="app">
    <img src="./assets/logo.png">
    <div>
      <button @click="startHacking">Start</button>
      <Drawer ref="drawer" :show-drawer.sync="showDrawer"></Drawer>
    </div>
  </div>
</template>

<script>
import Drawer from './Component/Drawer';
export default {
  name: "App",
  data () {
    return {
      showDrawer: true,
      demo: true
    };
  },
  components: {
    Drawer
  },
  methods: {
    startHacking() {
      console.log('startHacking');
      // this.showDrawer = !this.showDrawer;
      // this.demo = !this.demo;
      this.$refs.drawer.updateAnimation();
    }
  }
};
</script>
<style>
button {
  position: absolute;
  bottom: 0px;
}
#app {
  font-family: Helvetica, sans-serif;
  text-align: center;
}
</style>
