<template>
  <div class="search">
    <div class="negative">
          <h3>MusicPlayer</h3>
          <input type="text" class="search" v-model="searchSong" @keyup.enter="emitsearch">
          <button @click="emitsearch">
             <i class="fa fa-search"></i>
          </button>
        </div>
  </div>
</template>

<script>
import axios from "axios";
import {ref} from "vue";
export default {
    name: "Search",
    setup (props,context) {
      const searchSong = ref("");
      const emitsearch = () => {
          axios.get('http://192.168.1.105:3000/search?keywords='+ searchSong.value)
          .then(function(response) {
              context.emit("search", response.data.result.songs);
              searchSong.value = "";
            })
          .catch(function(err) {console.log(err);});
      };
      return{
        searchSong,
        emitsearch,
      };
    }
}
</script>

<style>
.negative {
  background-color: #c20c0c;
  border-radius: 8px 8px 0 0;
  position: relative;
  display: flex;
  align-items: center;
}

.negative h3 {
  margin: 12px 8px;
  font-size: 18px;
  color: white;
}

.negative input {
  position: absolute;
  height: 50%;
  border: none;
  border-radius: 6px;
  outline: none;
  right: 8px;
  padding: 4px;
}

.negative button {
  position: absolute;
  right: 10px;
  border: none;
  outline: none;
  cursor: pointer;
}
</style>