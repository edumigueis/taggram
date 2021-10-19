<template>
  <div id="app">
    <Modal @close="closeModal" v-show="isModalVisible" title="Ops... Algo deu errado." message="Estamos com problemas, tente novamente mais tarde."/>
    <div v-if="currentUser">
      <Header :currentUser="currentUser"></Header>
    </div>
    <div id="main-app-container">
      <div class="wrapper">
        <div v-if="post" class="wrapper-item wrapper-item-big">
          <img :src="post.photo" alt="Post Photo" />
        </div>
        <Comments @error="showModal" v-if="post && currentUser" :post="post" :currentUser="currentUser" />
      </div>
      <MorePosts v-if="post" :postUuid="post.uuid"></MorePosts>
      <Footer />
    </div>
  </div>
</template>

<script>
import Modal from "./components/Modal.vue";
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import Comments from "./components/Comments.vue";
import MorePosts from "./components/MorePosts.vue";

export default {
  name: "App",
  components: {
    Modal,
    Header,
    Footer,
    Comments,
    MorePosts,
  },
  data() {
    return {
      currentUser: {},
      post: null,
      isModalVisible: false,
    };
  },
  methods: {
    getUser: function () {
      fetch("https://taggram.herokuapp.com/me")
        .then((res) => res.json())
        .then((data) => ((this.currentUser = data), this.getPost()))
        .catch((err) => (this.showModal(), console.log(err)));
    },
    getPost: function () {
      fetch(
        "https://taggram.herokuapp.com/post?username=" +
          this.currentUser.username
      )
        .then((res) => res.json())
        .then((data) => (this.post = data))
        .catch((err) => (this.showModal(), console.log(err)));
    },
    showModal: function(){
      this.isModalVisible = true;
    },
    closeModal: function(){
      this.isModalVisible = false;
    }
  },
  created() {
    this.getUser();
  },
};
</script>

<style>
/* width */
::-webkit-scrollbar {
  width: 8px;
}

/* Track */
::-webkit-scrollbar-track {
  border-radius: 5px;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #dbdbdb;
  border-radius: 5px;
}
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
