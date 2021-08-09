<template>
  <div class="nf-min-card" @mouseleave="$emit('leave')">
    <img v-bind="{src}" alt="" class="img">

    <div class="px-3 my-3">
      <div class="d-flex">
        <circle-button icon="fa fa-play" active @click="logClick('play')"/>
        <circle-button icon="fa fa-plus" @click="logClick('add')"/>
        <circle-button icon="far fa-thumbs-up" @click="logClick('like')"/>
        <circle-button icon="far fa-thumbs-down" @click="logClick('dislike')"/>

        <circle-button icon="fa fa-chevron-down" style="margin-left: auto;" @click="$emit('maximize')"/>
      </div>

      <div class="mt-3">

        <span style="color: #42b983;">98% para tí</span>
        &nbsp;<span style="display: inline-block; padding: 2px; border: white 1px solid;">TV-MA</span>
        &nbsp;<span>2h 19 min</span>

      </div>

      <div class="mt-3">

        <span class="tag" v-for="tag in tags">
          <span class="tag-text">{{tag}}</span>
          <span class="tag-separator px-1">&bull;</span>
        </span>

      </div>
    </div>

  </div>
</template>

<script lang="ts">
import {Vue, Component, Prop} from 'vue-property-decorator'
import CircleButton from "@/components/general/CircleButton.vue";
import IDictionary from "@/interfaces/IDictionary";
import logClick from "@/utils/log-clicks";

@Component({
  name: "NfMinCard",
  components: {CircleButton}
})
export default class NfMinCard extends Vue
{
  @Prop({type: Object, default: () => ({})}) item!: IDictionary

  logClick = logClick

  get src()
  {
    let src = this.item.image;
    return src
  }

  get tags()
  {
    return this.item.tags || []
  }
}
</script>

<style scoped lang="scss">
  .nf-min-card
  {
    border-radius: 10px;
    width: 350px;
    overflow: hidden;
    box-shadow: 0px 0px 15px 1px #000000;

    .img {
      width: 100%;
      display: inline-block;
    }

    .tag
    {

      font-size: .8rem;

      &:last-child
      {
        .tag-separator
        {
          display: none;
        }
      }
    }
  }
</style>