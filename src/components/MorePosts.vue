<template>
  <div class="container">
      <h3 class="title">Mais publicações</h3>
    <div class="grid" v-if="relatedList.length > 0">
      <div class="img-wrapper" v-for="(related, i) in relatedList" :key="i">
        <img :src="related.photo" alt="Recommended Picture" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MorePosts",
  props: ["postUuid"],
  data(){
      return {relatedList: []}
  },
  created() {
            fetch(`https://taggram.herokuapp.com/posts/${this.postUuid}/related`)
                .then((res) => res.json())
                .then((data) => (this.relatedList = data.filter(r => r.comment_count >= 3)))
                .catch((err) => console.log(err));
  }
};
</script>

<style scoped>
.container{
    margin-top: 60px;
}

.grid {
  width: 100%;
  display: grid;
  grid-column-gap: 46px;
  grid-row-gap: 46px;
  grid-template-columns: repeat(3, 1fr);
}

.img-wrapper > img {
  object-fit: cover;
  width: 100%;
  max-height: 100%;
}

.title{
    font-size: 14px;
    font-weight: 700;
    margin-bottom: 20px;
    color: #8e8e8e !important;
    text-align: left;
}
</style>