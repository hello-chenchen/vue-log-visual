<template>
<div>
  <transition name="drawer-fade">
    <div v-show="visible" class="drawer__wrapper" style="z-index: 100">
      <div
        class="drawer__container"
        :class="visible && 'drawer__open'"
        @click.self="handleWrapperClick"
      >
        <div class="drawer ttb">
          <header>test header</header>
          <span>test text</span>
        </div>
      </div>
    </div>
  </transition>
<div v-show="visible" class="modal" style="z-index: 99;"></div>
</div>
</template>
<script>
export default {
  name: "Drawer",
  data() {
    return {};
  },
  props: {
    visible: {
      type: Boolean,
      default: false
    },
    beforeClose: {
      type: Function
    }
  },
  methods: {
    hide(cancel) {
      if (cancel !== false) {
        this.$emit("update:visible", false);
        this.$emit("close");
        if (this.destroyOnClose === true) {
          this.rendered = false;
        }
        this.closed = true;
      }
    },
    handleWrapperClick() {
        this.closeDrawer();
    },
    closeDrawer() {
      if (typeof this.beforeClose === "function") {
        this.beforeClose(this.hide);
      } else {
        this.hide();
      }
    }
  }
};
</script>
<style>
@-webkit-keyframes el-drawer-fade-in {
  0% {
    opacity: 0;
  }

  100% {
    opacity: 1;
  }
}

@keyframes el-drawer-fade-in {
  0% {
    opacity: 0;
  }

  100% {
    opacity: 1;
  }
}

@keyframes ttb-drawer-in {
  0% {
    -webkit-transform: translate(0, -100%);
    transform: translate(0, -100%);
  }

  100% {
    -webkit-transform: translate(0, 0);
    transform: translate(0, 0);
  }
}

@-webkit-keyframes ttb-drawer-out {
  0% {
    -webkit-transform: translate(0, 0);
    transform: translate(0, 0);
  }

  100% {
    -webkit-transform: translate(0, -100%);
    transform: translate(0, -100%);
  }
}

@keyframes ttb-drawer-out {
  0% {
    -webkit-transform: translate(0, 0);
    transform: translate(0, 0);
  }

  100% {
    -webkit-transform: translate(0, -100%);
    transform: translate(0, -100%);
  }
}

.drawer-fade-enter-active {
  -webkit-animation: el-drawer-fade-in 0.3s;
  animation: el-drawer-fade-in 0.3s;
}

.drawer-fade-leave-active {
  animation: el-drawer-fade-in 0.3s reverse;
}

.modal {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    opacity: .5;
    background: #000;
}

.drawer {
  left: 0;
  right: 0;
  width: 100%;
  height: 80%;
  position: absolute;
  box-sizing: border-box;
  background-color: #fff;
  display: flex;
  -ms-flex-direction: column;
  flex-direction: column;
  -webkit-box-shadow: 0 8px 10px -5px rgba(0, 0, 0, 0.2),
    0 16px 24px 2px rgba(0, 0, 0, 0.14), 0 6px 30px 5px rgba(0, 0, 0, 0.12);
  box-shadow: 0 8px 10px -5px rgba(0, 0, 0, 0.2),
    0 16px 24px 2px rgba(0, 0, 0, 0.14), 0 6px 30px 5px rgba(0, 0, 0, 0.12);
}

.drawer__wrapper {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  overflow: hidden;
  margin: 0;
}

.drawer__container {
  position: relative;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  height: 100%;
  width: 100%;
}

.drawer__open .drawer.ttb {
  -webkit-animation: ttb-drawer-in 0.3s 1ms;
  animation: ttb-drawer-in 0.3s 1ms;
}

.drawer.ttb {
  -webkit-animation: ttb-drawer-out 0.3s;
  animation: ttb-drawer-out 0.3s;
  top: 0;
}
</style>