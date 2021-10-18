<template>
  <div class="container">
    <img src="../assets/images/taggram.svg" alt="" />
    <div class="side-wrapper">
      <h1>{{ currentUser.username }}</h1>
      <div class="image">
        <img
          v-if="currentUser.avatar"
          :src="currentUser.avatar"
          alt="User Avatar"
        />
        <img v-else src="../assets/icons/user.jpg" alt="User Avatar" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  props: ["currentUser"],
};
</script>

<style scoped>
.container {
  width: 100%;
  padding: 0 10vw;
  background-color: white;
  border-bottom: 1px solid #dbdbdb;
  height: 54px;
  margin-bottom: 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.image {
  border-radius: 50%;
  width: 22px;
  height: 22px;
  overflow: hidden;
}

.image img {
  width: inherit;
  height: inherit;
}

h1 {
  font-weight: 400;
  font-size: 14px;
  padding-right: 12px;
}

.side-wrapper{
  display: flex;
  align-items: center;
}
</style>