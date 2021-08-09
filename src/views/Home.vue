<template>
  <div class="home">
    <nf-card-modal v-bind="{item}"/>
    <!--<nf-min-card :item="{
      image: 'https://i.blogs.es/16e585/breaking-bad/1366_2000.jpg',
      tags: [
          'Acción',
          'Narcos'
      ]
    }"/>-->
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from '@/components/HelloWorld.vue';
import NfVideoItem from "@/components/card/NfVideoItem.vue";
import NfMinCard from "@/components/card/NfMinCard.vue";
import NfCardModal from "@/components/card/NfCardModal.vue"; // @ is an alias to /src

@Component({
  components: {
    NfCardModal,
    NfMinCard,
    NfVideoItem,
    HelloWorld,
  },
})
export default class Home extends Vue {
  item = {
    image: 'https://i.blogs.es/16e585/breaking-bad/1366_2000.jpg',
    tags: [
      'Acción',
      'Narcos'
    ],
    description: `Walter White (Bryan Cranston) es un frustrado profesor de química en un instituto,
    padre de un joven discapacitado y con una mujer (Anna Gunn) embarazada.`,
    actors: [
        'Bryan Cranston',
        'Anna Gunn'
    ]
  }
}
</script>
