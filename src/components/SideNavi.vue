<template>
  <div>
    <div class="left-padding">
      <img class="logo" src="../assets/logo.png" alt="">
      <div class="flex icon-field" @click="$route.push('/home')">
        <img class="icon" src="../assets/home.png" alt="">     
        <p>ホーム</p>
      </div>
      <div class="flex icon-field" @click="$route.push('/profile')">
        <img class="icon" src="../assets/profile.png" alt="">
        <p>プロフィール</p>
      </div>
      <div class="flex icon-field" @click="$route.push('/logout')">
        <img class="icon" src="../assets/logout.png" alt="">
        <p>ログアウト</p>
      </div>
    </div>
    <hr />
    <ShareMessage />
  </div>  
</template>

<script>
import ShareMessage from '../components/ShareMessage.vue';

export default {
  components: {
    ShareMessage
  }  
};
</script>

<style scoped>
.left-padding {
  margin: 20px;
}
.flex {
  display: flex;
}
.logo {
  width: 100px;
}
.icon-field {
  margin-top: 15px;
  cursor: pointer;
}
.icon {
  width: 25px;
}
.icon-field p {
  font-size: 16px;
  margin-top: 6px;
  padding-left: 15px;
}
hr {
  border: black;
}
</style>