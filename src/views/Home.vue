<template>
  <div class="home">
    <itemcontainer father-component="home"/>
  </div>
</template>

<script>
// @ is an alias to /src
import itemcontainer from '@/components/itemcontainer.vue'

export default {
  name: 'home',
  components: {
    itemcontainer
  }
}
</script>
