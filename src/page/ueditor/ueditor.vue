<template>
  <div>
    <div id="editor"></div>
    <button type="" @click="gettext">点击</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      editor: null
    }
  },
  mounted () {
    // // 引入url
    // UEDITOR_CONFIG.UEDITOR_HOME_URL = '../../static/Ueditor/'
    // // 实例化editor编辑器
    // this.editor = UE.getEditor('editor')
  },
  methods: {
    gettext () {
      // 获取editor中的文本
      console.log(this.editor.getContent())
    }
  },
  destroyed () {
    // 将editor进行销毁
    this.editor.destroy()
  }
}
</script>
