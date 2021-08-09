<template>
  <div class="nf-video-item">
    <div :style="stylesThumbnail" class="nf-thumbnail-card nf-full">
    </div>
  </div>
</template>

<script lang="ts">
import {Vue, Component} from "vue-property-decorator";

@Component({
  name: "NfVideoItem"
})
export default class NfVideoItem extends Vue
{
  src = 'https://i.blogs.es/16e585/breaking-bad/1366_2000.jpg'

  get stylesThumbnail()
  {
    return {
      backgroundImage: `url('${this.src}')`
    }
  }
}
</script>

<style scoped lang="scss">
  .nf-video-item
  {
    display: inline-block;
    width: 200px;
    height: 150px;

    .nf-thumbnail-card
    {
      background-size: 100% 100%;
      border-radius: 2px;
    }
  }
</style>