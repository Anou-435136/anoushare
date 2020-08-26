<template>
  <div class="flex">
    <div class="left">
      <SideNavi />    
    </div>
    <div class="right">
      <div class="title">
        <p>ホーム</p>
      </div>
      <Message />      
    </div>
  </div>
</template>

<script>
import SideNavi from '../components/SideNavi.vue';
import Message from '../components/Message.vue';

export default {
  data() {
    return {
      shares: [{ name: "ノア", like: [], share: "初めまして" }]
    };
  },
  components: {
    SideNavi,
    Message
  }
}
</script>

<style scoped>
.left {
  width: 22%;
  height: 100vh;
}
.right {
  width: 78%;
  height: 100vh;
}
.flex {
  display: flex;
}
.title {
  border-bottom: 1px solid white;
  border-left: 1px solid white;
  padding: 15px;
}
.title p {
  font-size: 20px;
  font-weight: bold;
}
.share-message {
  border: 1px solid white;
}
.left-padding {
  margin: 20px;
}
.logo {
  width: 100px;
}
.icon-field {
  margin-top: 15px;
  cursor: pointer;
}
.icon-field p {
  font-size: 16px;
  padding-left: 15px;
}
.share {
  margin: 15px;
}
.share textarea {
  width: 95%;
  height: 120px;
  margin: 15px 0;
  border-radius: 10px;
  border: 1px solid white;
  background-color: #15202b;
  color: white;
  resize: none;
}
button {
  width: 100px;
  text-align: center;
  padding: 8px 0 10px;
  color: white;
  background-color: #5419da;
  border-radius: 25px;
  display: block;
  margin-left: auto;
}
.header {
  text-align: center;
  margin-top: 20px;
  padding-bottom: 10px;
  border-bottom: 1px solid white;
}
.icon {
  width: 25px;
  height: 25px;
}
.detail {
  margin-left: 50px;
}
.message {
  padding: 20px;
  border-bottom: 1px solid white;
  border-left: 1px solid white;
}
.name {
  font-size: 18px;
  font-weight: bold;
  margin-right: 10px;
}
.text {
  margin-top: 10px;
}
.number {
  margin: 0 10px 0;
}
</style>