<template>
  <div class="about">
    <h1>This is an about page</h1>
    <box :msg="msg"></box>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Box from '@/components/Box.vue'; // @ is an alias to /src

@Component({
  components: {
    Box,
  },
})
export default class About extends Vue {
  public msg: string = 'quda!';
}
</script>
