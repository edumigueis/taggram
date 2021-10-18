<template>
  <div class="container">
      <h3 class="title">Mais publicações</h3>
    <div class="grid">
      <div class="img-wrapper">
        <img src="../assets/images/1.jpg" alt="Recommended Picture" />
      </div>
      <div class="img-wrapper">
        <img src="../assets/images/2.jpg" alt="Recommended Picture" />
      </div>
      <div class="img-wrapper">
        <img src="../assets/images/3.jpg" alt="Recommended Picture" />
      </div>
      <div class="img-wrapper">
        <img src="../assets/images/4.jpg" alt="Recommended Picture" />
      </div>
      <div class="img-wrapper">
        <img src="../assets/images/5.jpg" alt="Recommended Picture" />
      </div>
      <div class="img-wrapper">
        <img src="../assets/images/6.jpg" alt="Recommended Picture" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MorePosts",
  props: {},
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