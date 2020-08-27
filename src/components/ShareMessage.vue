<template>
  <div class="share">
    <p>シェア</p>
    <textarea></textarea>
    <div>
      <button>シェアする</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      share: ''
    };
  },
  methods: {
    send() {
      if (this.share === '') {
        alert('シェアする内容を入力してください');
      } else {
        axios
        .post('herokuのurl/api/shares', {
          user_id: this.$store.state.user.id,
          share: this.share
        })
        .then((response) => {
          console.log(response);
          alert('シェアしました');
          this.share = '';
          this.$router.go({
            path: this.$router.currentRoute.path,
            force: true
          });
        });
      }
    }
  }
};
</script>

<style scoped>
.share {
  margin: 15px;
}
.share textarea {
  width: 95%;
  height: 120px;
  margin: 15px 0 15px;
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
  border-radius: 10px;
  display: block;
  margin: 0 0 0 auto;
}
</style>