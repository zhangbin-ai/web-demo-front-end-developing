<template>
  <div class="home">
    <H1>Home</H1>
    <my-icon iconClass="shouye" color="#00ff00" size="140px"/>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'Home',
  computed: {
    ...mapGetters([
      'name'
    ])
  }
}
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
</style>
