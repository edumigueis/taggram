<template>
  <div class="container">
    <div class="image">
      <img v-if="post.user.avatar" :src="post.user.avatar" alt="User Avatar" />
      <img v-else src="../assets/icons/user.jpg"
          alt="User Avatar"/>
    </div>
    <div class="text-data" v-if="post">
      <h3>{{post.user.username}}</h3>
      <h4>{{post.location.city}}, {{post.location.country}}</h4>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserData",
  props: ["post"]
};
</script>

<style scoped>
.container {
  display: flex;
  align-items: center;
  padding: 20px 0 20px 17px;
  border-bottom: 1px solid #dbdbdb;
}
.image {
  border-radius: 50%;
  width: 32px;
  height: 32px;
  overflow: hidden;
}

.image > img {
  object-fit: cover;
  width: inherit;
  height: inherit;
}

.text-data > h3 {
  font-size: 14px;
  font-weight: 700;
  margin: 0;
}
.text-data > h4 {
  font-size: 12px;
  font-weight: 400;
  margin: 0;
  line-height: 18px;
}

.text-data {
  padding-left: 16px;
}
</style>