<template>
  <div class="comment">
      <CommentItem v-for="comment in comments" :key="comment.commentId" :comment="comment"></CommentItem>
  </div>
</template>

<script>
import {watch,ref} from 'vue'
import axios from 'axios'
import CommentItem from "./CommentItem"
export default {
    name: "Comments",
    components: {CommentItem},
    props: ["current"],
    setup (props) {
      const comments = ref([]);
      const getcomments = watch ( () => {
        axios.get("http://localhost:3000/comment/music?id="+props.current.id)
        .then(function(response){console.log(response.data.hotComments); comments.value = [...response.data.hotComments];})
        .catch(function(err) {console.log(err);});
      });
      return{
        getcomments,
        comments,
        props,
      };
    }
}
</script>

<style>
.comment li{
  border-bottom: 1px dotted rgba(247,247,247,0.6);
}

.comment {
  width: 25%;
  overflow: scroll;
}
</style>