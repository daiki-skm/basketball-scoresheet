<template>
  <div class="home">
    <Scoresheet></Scoresheet>
  </div>
</template>

<script>
// @ is an alias to /src
import Scoresheet from '@/components/Scoresheet.vue'

export default {
  name: 'Home',
  components: {
    Scoresheet
  }
}
</script>
