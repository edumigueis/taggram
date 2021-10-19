<template>
  <div class="modal-wrapper">
      <div class="modal-container">
          <div class="modal">
              <div class="top">
                  <h1>{{title}}</h1>
                  <p>{{message}}</p>
              </div>
              <div class="bottom" v-on:click="close">
                  <h2>
                     Close
                  </h2>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: ["message", "title"],
  methods: {
      close() {
        this.$emit('close');
      },
    },
};
</script>

<style scoped>
    .modal-wrapper{
        background-color: #232323aa;
        height: 100vh;
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
        z-index: 1000;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .modal-container{
        position: relative;
        background-color: white;
        width: 60%;
        max-width: 480px;
        min-width: 320px;
        height: 200px;
    }
    .bottom{
        position: absolute;
        bottom: 0;
        display: flex;
        align-items: center;
        justify-content: center;
        height: 50px;
        border-top: 1px solid #dbdbdb;
        width: 100%;
    }
    .bottom:hover{
        background-color: #e5e5e5;
        cursor: pointer;
    }
    .bottom h2{
        font-size: 14px;
        font-size: 500;
    }
    .top{
        padding: 0 16px;
    }
    .top h1{
        font-size: 16px;
        font-weight: 700;
        text-align: center;
        margin: 0;
        padding: 20px 0 4px 0;
    }
    .top p{
        font-size: 14px;
        text-align: center;
        font-weight: 400;
    }
</style>