<template>
  <div class="home">
    <Jitsi />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Jitsi from '@/components/Jitsi.vue'; // @ is an alias to /src

@Component({
  components: {
    Jitsi,
  },
})
export default class HomeView extends Vue {}
</script>

<style lang="scss">
.home{
  height: calc(100vh - 100px);
}
</style>