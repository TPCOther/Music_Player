<template>
  <main :style="cover">
    <div class="wrap">
    <div class="container">
        <Search @search="updatelist"></Search>
        <div class="menu">
         <MusicList :list="musiclist"></MusicList>
          <MusicDetails :current="currentsong"></MusicDetails>
          <Comments :current="currentsong"></Comments>
        </div>
        <Progress :current="currentsong"></Progress>
    </div>
    </div>
  </main>
</template>

<script>
import {computed, ref, provide} from "vue";
import axios from "axios";
import MusicList from "./components/MusicList";
import Comments from "./components/Comments";
import MusicDetails from "./components/MusicDetails";
import Search from "./components/Search";
import Progress from "./components/Progress";
export default {
  name: 'App',
  components : {MusicList, Comments, MusicDetails, Search, Progress},
  setup() {
    const musiclist = ref([]);
    const currentsong = ref({});
    const cover = computed(() => {
      if(currentsong.value.al) {return {backgroundImage: 'url('+ currentsong.value.al.picUrl+')',backgroundRepeat:'no-repeat',backgroundSize:'100% 100%',objectFit: 'cover'};}
      else{return {};}
    })
    const updatelist = (newlist) => {musiclist.value = [...newlist];}
    const switchmusic = (val) => {
      axios.get("http://localhost:3000/song/detail?ids="+val)
      .then(function(response) {currentsong.value = response.data.songs[0];})
      .catch(function(err) {console.log(err);});
    }
    provide('switchmusic',switchmusic);
    return{
      musiclist,
      updatelist,
      currentsong,
      switchmusic,
      cover,
    };
  },
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: Helvetica, "PingFang SC", "Microsoft Yahei", sans-serif;
}

main {
  width: 100vw;
  height: 100vh;
  display: grid;
  place-items: center;
  background: #E6DADA;
  background: -webkit-linear-gradient(to right, #274046, #E6DADA);
  background: linear-gradient(to right, #274046, #E6DADA);
}

.wrap {
  width:100vw;
  height: 100vh;
  display: grid;
  place-items: center;
  background:rgba(0, 0, 0, 0.5);
}

.container {
  width: 70%;
  box-shadow: 0px 0px 24px rgba(0,0,0,0.15);
}

.menu {
  display: flex;
  height: 60vh;
  backdrop-filter: blur(8px);
  background-color: rgba(255, 255, 255, 0.1);
}
</style>
