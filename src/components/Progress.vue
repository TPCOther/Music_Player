<template>
  <div class="progress">
          <meta http-equiv="Access-Control-Allow-Origin" content="*">
          <audio :src="geturl" controls="controls"></audio>
  </div>
</template>

<script>
import {computed} from "vue";
export default {
    name: "Progress",
    props: ["current"],
    setup (props) {
      const geturl = computed (() => {
        return "https://music.163.com/song/media/outer/url?id=" + props.current.id + ".mp3";
      })
      return{geturl};
    }
}
</script>

<style>
.progress{
  height: 48px;
  background-color: white;
  border-radius: 0 0 8px 8px;
}

.progress audio{
  width: 100%;
  height: 100%;
  outline: none;
  background-color: rgb(241,243,244);
}
</style>