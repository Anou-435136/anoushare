<template>
  <div class="flex">
    <div class="left">
      <SideNavi />
    </div>
    <div class="right">
      <div class="title">
        <p>ホーム</p>
      </div>
      <Message :id="id" />
      <div class="comment">
        <div class="comment-title">
          <p>コメント</p>
        </div>
        <div class="message" v-for="(comment, index) in data" :key="index">
          <div class="flex">
            <p class="name">{{ comment.name }}</p>
          </div>
          <div>
            <p class="text">{{ comment.content }}</p>
          </div>
        </div>
        <input type="text" v-model="content">
        <div @click="send">
          <button>コメント</button>
        </div>
      </div>
    </div>
  </div>  
</template>

<script>
import SideNavi from '../components/SideNavi.vue';
import Message from '../components/Message.vue';
import axios from 'axios';

export default {
  props: ['id'],
  data() {
    return {
      data: '',
      content: '',
    };
  },
  components: {
    SideNavi,
    Message
  },
  methods: {
    send() {
      axios
      .post('herokuのurl/api/comment', {
        share_id: this.id,
        user_id: this.$store.state.user_id,
        content: this.content
      }) 
      .then((response) => {
        console.log(response);
        this.content = '';
        this.$router.go({
          path: this.$router.currentRoute.path,
          force: true
        });
      });
    },
    comment() {
      axios
      .get('herokuのurl/api.shares/' + this.id)
      .then((response) => {
        this.data = response.data.comment;
      });
    }
  },
  created() {
    this.comment();
  },
};
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
  border-bottom: 1px solid white;
}
.comment-title {
  text-align: center;
  padding-top: 10px;
  border-bottom: 1px solid white;
  border-left: 1px solid white;
}
.comment input {
  width: 95%;
  height: 30px;
  margin: 20px 0 15px 10px;
  border-radius: 10px;
  border: 1px solid white;
  background-color: #15202d;
  color: white;
}
.message {
  padding: 10px 0 10px 10px;
  border-bottom: 1px solid white;
  border-left: 1px solid white;
}
.text {
  margin-top: 10px;
  font-size: 10px;
}
button {
  width: 100px;
  text-align: center;
  padding: 8px 0 10px;
  color: white;
  background-color: #5419da;
  border-radius: 25px;
  display: block;
  margin: 0 0 0 auto;
}
</style>