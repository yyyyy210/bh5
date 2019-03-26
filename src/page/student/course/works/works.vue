<template>
  <div v-loading="loading">
    <Waterfall></Waterfall>
  </div>
</template>

<script>
import Waterfall from '../../../waterfall/waterfall.vue'
export default {
  name: 'Works',
  data () {
    return {
      loading: true
    }
  },
  created () {
    setTimeout(() => {
      this.loading = false
    }, 1000)
  },
  components: {
    Waterfall
  }
}
</script>

<style lang="scss" scoped>
</style>
