<template>
  <div id="app">
    <div v-if="currentUser">
      <Header :currentUser="currentUser"></Header>
    </div>
    <div id="main-app-container">
      <div class="wrapper">
        <div v-if="post" class="wrapper-item wrapper-item-big">
          <img :src="post.photo" alt="Post Photo" />
        </div>
        <Comments v-if="post" :post="post" />
      </div>
      <MorePosts></MorePosts>
      <Footer />
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import Comments from "./components/Comments.vue";
import MorePosts from "./components/MorePosts.vue";

export default {
  name: "App",
  components: {
    Header,
    Footer,
    Comments,
    MorePosts,
  },
  data() {
    return {
      currentUser: {},
      post: null,
    };
  },
  methods: {
    getUser: function () {
      fetch("https://taggram.herokuapp.com/me")
        .then((res) => res.json())
        .then((data) => ((this.currentUser = data), this.getPost()))
        .catch((err) => console.log(err));
    },
    getPost: function () {
      fetch(
        "https://taggram.herokuapp.com/post?username=" +
          this.currentUser.username
      )
        .then((res) => res.json())
        .then((data) => ((this.post = data), console.log(this.post)))
        .catch((err) => console.log(err));
    },
  },
  created() {
    this.getUser();
  },
};
</script>

<style>
body {
  overflow-x: hidden;
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #262626;
  margin: 0;
  width: 100vw;
  background-color: #e5e5e5;
}
* {
  box-sizing: border-box;
}
#main-app-container {
  margin: 0 10vw 0 10vw;
  overflow: hidden;
  width: 80vw;
}
.wrapper {
  background-color: white;
  display: flex;
  flex-wrap: nowrap;
  flex-flow: row;
}

.wrapper > .wrapper-item-big {
  flex: calc(66.6666666% - 23px);
}
.wrapper > .wrapper-item-small {
  flex: calc(33.4%);
}
.wrapper > .wrapper-item {
  overflow: hidden;
  max-height: 600px;
}

.wrapper-item > img {
  width: 100%;
  object-fit: cover;
}
</style>
