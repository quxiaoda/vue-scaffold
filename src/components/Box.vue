<template>
  <div class="box">
      <span class="content">{{ content }}</span>
  </div>
</template>

<style lang="scss" scoped>
    .box {
        width: 100px;
        height: 100px;
        line-height: 100px;
        text-align: center;
        background: #cccccc;
        .content {
            font-size: 10px;
            color: #ffffff;
        }
    }
</style>

<script lang="ts">
import {Component, Vue, Prop} from 'vue-property-decorator';

@Component
export default class Box extends Vue {
     // undecorated property will be packed in `data` option
    public defaultContent = 'Hello';

    @Prop({default: 'World'})
    public msg: string;

    // Computed properties are written as getters and setters on the class.
    get content() {
        return this.defaultContent + ' ' + this.msg;
    }
}
</script>


