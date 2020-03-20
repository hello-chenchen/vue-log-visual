<template>
  <div v-show="showDrawer" class="drawer" :style="animationDirection">
    <button aria-label="close" type="button" class="el-drawer__close-btn"><i class="el-dialog__close el-icon el-icon-close"></i></button>
      <span>test text</span>
  </div>
</template>
<script>
export default {
  name: "Drawer",
  data () {
    return {
      animationDirection: "animation-name: t2b-drawer-out; height:0%",
      animationDirectionList: ["animation-name: t2b-drawer-in; height:80%", "animation-name: t2b-drawer-out; height:0%"]
    }
  },
  props: {
    showDrawer: {
      type: Boolean,
      default: false
    },
    animation: {
      type: String,
      default: "animation-name: t2b-drawer-out; height:0%"
    }
  },
  methods: {
    updateAnimation() {
      // if(false == val) {
      //   this.animationDirection = "animation-name: t2b-drawer-out; height:0%";
      // } else {
      //   this.animationDirection = "animation-name: t2b-drawer-in; height:80%";
      // }
      this.animationDirection = "animation-name: t2b-drawer-out; height:0%";
    }
  }
};
</script>
<style>
.drawer {
  background-color: gray;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 80%;
  z-index: 999;
  color: #fff;
  animation-duration: 500ms;
  animation-timing-function: cubic-bezier(0, 0, 0.2, 1);
  animation-delay: 0ms;
  animation-iteration-count: 1;
  animation-direction: normal;
  animation-fill-mode: none;
  animation-play-state: running;
}

@keyframes t2b-drawer-in {
    0% {
        transform: translateY(-100%)
    }
    to {
        transform: translate(0)
    }
}

@keyframes t2b-drawer-out {
    0% {
        transform: translate(0)
    }

    to {
        transform: translateY(-100%)
    }
}
</style>