<template>
  <div class="nf-video-item position-relative">
    <div :style="stylesThumbnail" class="nf-thumbnail-card nf-full" @mouseenter="mode = ViewerModeEnum.CARD">
    </div>

    <div class="position-absolute" style="top: 0; left: 0;" v-if="mode === ViewerModeEnum.CARD">
      <nf-min-card v-bind="{item}" @leave="mode = ViewerModeEnum.THUMBNAIL" @maximize="mode = ViewerModeEnum.MODAL"/>
    </div>

    <nf-card-modal v-bind="{item}" v-if="mode === ViewerModeEnum.MODAL" @close="mode = ViewerModeEnum.THUMBNAIL"/>
  </div>
</template>

<script lang="ts">
import {Component, Prop, Vue} from "vue-property-decorator";
import ViewerModeEnum from "@/enums/ViewerModeEnum";
import IDictionary from "@/interfaces/IDictionary";
import NfMinCard from "@/components/card/NfMinCard.vue";
import NfCardModal from "@/components/card/NfCardModal.vue";

@Component({
  name: "NfVideoItem",
  components: {NfCardModal, NfMinCard}
})
export default class NfVideoItem extends Vue
{
  @Prop({type: Object, default: () => ({})}) item!: IDictionary
  private mode: ViewerModeEnum = ViewerModeEnum.THUMBNAIL;
  ViewerModeEnum = ViewerModeEnum;

  get stylesThumbnail()
  {
    let src = this.item.image
    return {
      backgroundImage: `url('${src}')`
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