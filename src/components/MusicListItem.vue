<template>
      <li>{{music.name}}<i class="fa fa-play-circle-o fa-lg" @click="switchmusic(music.id)"></i></li>
</template>

<script>
import {inject} from 'vue'
export default {
    name: "MusicListItem",
    props: ["music"],
    setup () {
      const switchmusic = inject('switchmusic');
      return {switchmusic};
    }
}
</script>

<style>
li{
  color: white;
  position: relative;
  display: block;
  padding: 8px;
}

li i{
  color: rgb(80,82,88);
  position: absolute;
  right: 8px;
  cursor: pointer;
}

li i:hover{
  color: #c20c0c;
}
</style>