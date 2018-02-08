<template>
  <div class="hello">
    <cube-button @click="showBtn">Dialog - btn</cube-button>
    <cube-button @click="showAlert">Dialog - type</cube-button>
    <cube-button @click="showToast">show toast</cube-button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      toastTxt: 'cube toast content'
    }
  },
  methods: {
    showToast () {
      this.$createToast({
        txt: this.toastTxt
      }).show()
    },
    showAlert () {
      this.$createDialog({
        type: 'alert',
        title: '我是标题',
        content: '我是内容',
        icon: 'cubeic-alert'
      }).show()
    },
    showBtn () {
      this.$createDialog({
        type: 'confirm',
        icon: 'cubeic-alert',
        title: '我是标题',
        content: '我是内容',
        confirmBtn: {
          text: '确定按钮',
          active: true,
          disabled: false,
          href: 'javascript:;'
        },
        cancelBtn: {
          text: '取消按钮',
          active: false,
          disabled: false,
          href: 'javascript:;'
        },
        onConfirm: () => {
          this.$createToast({
            type: 'warn',
            time: 1000,
            txt: '点击确认按钮'
          }).show()
        },
        onCancel: () => {
          this.$createToast({
            type: 'warn',
            time: 1000,
            txt: '点击取消按钮'
          }).show()
        }
      }).show()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
