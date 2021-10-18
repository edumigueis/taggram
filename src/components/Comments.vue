<template>
  <div class="wrapper-item wrapper-item-small">
    <div class="container comments">
      <UserData v-if="post.user" :post="post" />
      <div v-if="comments != null" class="comments-wrapper">
        <div v-for="comment in comments" :key="comment.uuid">
          <Comment :content="comment" :currentUser="currentUser"/>
        </div>
      </div>

      <Statistics v-if="post" :post="post" />
    </div>
  </div>
</template>

<script>
import UserData from "./UserData.vue";
import Comment from "./Comment.vue";
import Statistics from "./Statistics.vue";

export default {
  name: "Comments",
  components: {
    UserData,
    Statistics,
    Comment,
  },
  data() {
    return { comments: this.post.comments };
  },
  props: ["post", "currentUser"],
};
</script>

<style scoped>
.wrapper-item-small {
  border: 1px solid #dbdbdb;
}
.container.comments {
  position: relative;
  height: 100%;
}
.comments-wrapper{
  max-height: calc(100% - 145px);
  overflow-y: scroll;
}

/* width */
.comments-wrapper::-webkit-scrollbar {
  width: 8px;
}

/* Track */
.comments-wrapper::-webkit-scrollbar-track {
  border-radius: 5px;
}

/* Handle */
.comments-wrapper::-webkit-scrollbar-thumb {
  background: #dbdbdb;
  border-radius: 5px;
}
</style>