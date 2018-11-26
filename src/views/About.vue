<template>
  <div class="about">
    <itemcontainer father-component="item"/>
  </div>
</template>

<script>
// @ is an alias to /src
import itemcontainer from '@/components/itemcontainer.vue'

export default {
  name: 'about',
  components: {
    itemcontainer
  }
}
</script>
