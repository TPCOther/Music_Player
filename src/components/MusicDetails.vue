<template>
  <div class="disc">
            <div class="SongCover">
              <img :src="getcover">
              <span class="msk"></span>
            </div>
            <a v-if="current.al">{{current.al.name}}</a>
            <a v-else>Song</a>
  </div>
</template>

<script>
import {computed} from "vue";
export default {
    name: "MusicDetails",
    props: ["current"],
    setup(props) {
      const getcover = computed( () =>{
        if(props.current.al){return props.current.al.picUrl;}
        else{return "https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=646736655,4007166352&fm=26&gp=0.jpg";}
      });
      return{getcover};
    }
}
</script>

<style>
.disc {
  float: left;
  display: grid;
  place-items: center;
  width: 50%;
  height: 100%;
  position: relative;
}

.disc .SongCover {
  height: 200px;
  width: 200px;
}

.disc .SongCover img {
  height: 100%;
  width: 100%;
}

.disc .SongCover span{
  position: absolute;
  width: 208px;
  height: 208px;
  top: -4px;
  left: -4px;
}

.disc a {
  font-size: 24px;
  color: white;
}
</style>