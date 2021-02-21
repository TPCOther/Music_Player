<template>
      <li>{{music.name}}<i class="fa fa-play-circle-o fa-lg" @click="$emit('switchmusic', music.id)"></i></li>
</template>

<script>
export default {
    name: "MusicListItem",
    props: ["music"],
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