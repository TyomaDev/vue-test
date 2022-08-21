<template>
  <div class="MainPage">
    <!-- top block with a cover and user's info-->
      <InfoBlock/>
    <!-- /top block  -->

    <!-- block with photos -->
      <Photos/>
    <!-- /block with photos -->
        
  </div>

</template>

<script>

import InfoBlock from './components/Info-Block.vue'
import Photos from './components/User-Photos.vue'


export default {
  name: 'App',
  components: {
    InfoBlock,
    Photos
  },
  

}
</script>

<style>

</style>
