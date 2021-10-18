<template>
  <div class="container">
    <h4>{{post.comments.length}} comentários</h4>
    <h6>22/04/2020 - 9:10</h6>
  </div>
</template>

<script>
export default {
  name: 'Statistics',
  props: ["post"],
   created() {
    console.log(this.post.comments)  //undefined;
  },
}
</script>

<style scoped>
.container{
  width: 100%;
  padding: 16px 0;
  border-top: 1px solid #DBDBDB;
  padding-left: 17px;
  position: absolute;
  bottom: 0;
}

.container > h6{
  color: #8E8E8E;
  font-size: 11px;
  margin: 0;
  line-height: 18px;
}

.container > h4{
  font-size: 14px;
  font-weight: 700;
  margin: 0;
  line-height: 18px;
}
</style>