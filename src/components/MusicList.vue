<template>
       <div class="list">
            <MusicListItem v-for="item in list" :key="item.id" :music="item"></MusicListItem>
    </div>
</template>

<script>
import MusicListItem from "./MusicListItem"
export default {
    name:"MusicList",
    components: {MusicListItem},
    props: ["list"],
}
</script>

<style>

.list {
  width: 25%;
  height: 100%;
  overflow: auto;
  scrollbar-width: none;
  -ms-overflow-style: none;
}

::-webkit-scrollbar {
  display: none; /* Chrome Safari */
}

.list li:nth-child(odd){
  background-color: rgba(255,255,255,0.2);
}
</style>