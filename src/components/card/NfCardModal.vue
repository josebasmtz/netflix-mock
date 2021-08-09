<template>
  <div class="nf-card-modal">
    <div class="modal-diag d-flex">
      <div style="" class="mx-auto my-4 modal-container position-relative">
        <div style="position: relative">
          <img v-bind="{src}" alt="" style="height: 400px; width: 100%">

          <span class="position-absolute" style="bottom: 20px; left: 15px;">
            <button class="btn bg-white">
              <i class="fa fa-play"></i> Reproducir
            </button>

            <circle-button icon="fa fa-plus" style="margin-left: 10px;" @click="logClick('add')"/>
            <circle-button icon="far fa-thumbs-up" @click="logClick('like')"/>
            <circle-button icon="far fa-thumbs-down" @click="logClick('dislike')"/>
          </span>

          <span class="position-absolute" style="top: 20px; right: 15px;">
            <circle-button active icon="fa fa-times" @click="$emit('minimize')"/>
          </span>
        </div>


        <div class="px-3 my-3">
          <div class="row">
            <div class="col-7">

              <div>

                <span style="color: #42b983;">98% para tí</span>
                &nbsp;<span style="display: inline-block; padding: 2px; border: white 1px solid;">TV-MA</span>
                &nbsp;<span>2h 19 min</span>

              </div>

              <div class="mt-3">
                {{description}}
              </div>
            </div>
            <div class="col-5">
              <div>
                <span class="label">Elenco:</span> {{actors}}
              </div>
              <div class="mt-3">
                <span class="label">Géneros:</span> {{tags}}
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import {Vue, Component, Prop} from 'vue-property-decorator'
import IDictionary from "@/interfaces/IDictionary";
import CircleButton from "@/components/general/CircleButton.vue";
import logClick from "@/utils/log-clicks";

@Component({
  name: "NfCardModal",
  components: {CircleButton}
})
export default class NfCardModal extends Vue
{
  @Prop({type: Object, default: () => ({})}) item!: IDictionary;

  logClick = logClick

  get src()
  {
    return this.item.image;
  }

  get description()
  {
    return this.item.description
  }

  get tags()
  {
    let tags = this.item.tags || []
    return tags.join(', ')
  }

  get actors()
  {
    let actors = this.item.actors || []
    return actors.join(', ')
  }
}
</script>

<style scoped lang="scss">
  .nf-card-modal
  {
    position: fixed;

    left: 0;
    top: 0;
    right: 0;
    bottom: 0;

    overflow: auto;
    display: block !important;

    background: rgba(128, 128, 128, 0.14);

    .modal-container
    {
      position: relative;
      width: 600px;
      display: inline-block;
      border-radius: 10px;
      overflow: hidden;
      box-shadow: 0px 0px 15px 1px #000000;
    }

    .label {
      color: gray;
    }
  }
</style>