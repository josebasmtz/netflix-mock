<template>
  <span class="nf-circle-button" @click="$emit('click', $event)" :class="{active}">
    <i :class="[icon]" class="icon"></i>
  </span>
</template>

<script lang="ts">
import {Vue, Component, Prop} from 'vue-property-decorator'

@Component({
  name: "CircleButton"
})
export default class CircleButton extends Vue
{
  @Prop({type: String, default: ''}) icon!: string
  @Prop({type: Boolean, default: false}) active!: boolean
}
</script>

<style scoped lang="scss">
  .nf-circle-button
  {
    position: relative;
    border: 1px white solid;
    border-radius: 50%;
    height: 45px;
    width: 45px;

    display: inline-block;

    cursor: pointer;

    &.active
    {
      color: black;
      background: white;

      &:hover {
        color: white;
        background: rgba(255, 255, 255, 0.70);
      }
    }

    &:hover:not(.active)
    {
      background: rgba(255, 255, 255, 0.20);
    }

    .icon
    {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translateX(-50%) translateY(-50%);
    }
  }
</style>