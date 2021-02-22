<template>
<li>
    <div class="info">
      <img :src="comment.user.avatarUrl" class="avatar"> 
        <p class="CoName">{{comment.user.nickname}}</p>
    </div>
    <p class="CoContent">{{comment.content}}</p>
</li>
</template>

<script>
export default {
    name: "CommentItem",
    props: ['comment'],
}
</script>

<style>
.avatar {
  float: left;
  height: 48px;
  width: 48px;
  border-radius: 50%;
}

.info {
  height:60px;
}

.CoName{
  float: left;
  padding: 8px 8px 8px 12px;
  font-weight: bold;
  color: white;
}

.CoContent{
  padding: 0px 8px 8px 8px;
  color: White;
  font-size: 14px;
}
</style>