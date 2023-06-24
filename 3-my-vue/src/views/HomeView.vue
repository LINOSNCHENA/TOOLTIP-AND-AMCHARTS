<template>
  <div class="home">
    <Plotx msg="Welcome to Your Vue.js + TypeScript App"/>
    <Pemba msg="Welcome to Pemba + TypeScript App"/>
    <zlin-town msg="Welcome to Zlin + TypeScript App"/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Plotx from '@/components/PembaPlot.vue'; 
import Pemba from '@/components/PembaBar.vue'; 
import ZlinTown from '@/components/PembaPiechart.vue';

export default defineComponent({
  name: 'HomeView',
  components: {
    Plotx,
    Pemba,
    ZlinTown
  },
});
</script>
