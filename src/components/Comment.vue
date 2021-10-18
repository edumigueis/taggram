<template>
  <div class="container flex">
    <div class="img-wrapper">
      <div class="image">
        <img
          v-if="content.user.avatar"
          :src="content.user.avatar"
          alt="User Avatar"
        />
      </div>
    </div>
    <div class="text-data">
      <div class="flex">
        <p>
          <span class="username">{{ content.user.username }}</span>
          <span class="message">{{ content.message }}</span>
        </p>
      </div>
      <div class="bottom-text">
        <h6 class="time">{{ content.created_at }}</h6>
        <h6 class="likes">{{ content.like_count }}</h6>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Comment",
  props: ["content"],
};
</script>

<style scoped>
.container {
  margin-top: 32px;
}

.flex {
  display: flex;
  flex-flow: row;
  flex-wrap: nowrap;
}

.container h2,
p,
h6 {
  margin: 0;
}
.container .username {
  font-size: 14px;
  font-weight: 700;
}

.message {
  font-size: 14px;
  font-weight: 400;
}
.img-wrapper {
  flex: 66px;
  padding: 0 17px;
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

.text-data {
  flex: calc(100% - 66px);
}

.bottom-text {
  display: flex;
  flex-wrap: nowrap;
  padding-top: 16px;
}
.bottom-text h6 {
  padding-right: 12px;
  color: #8e8e8e;
  font-size: 14px;
  font-weight: 400;
}
</style>