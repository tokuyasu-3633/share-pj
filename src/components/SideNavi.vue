<template>
  <div>
      <div class="menu">
        <img src="../assets/logo.png" class="menu-logo">
        <ul class="menu-list">
          <li>
            <img src="../assets/home.png">
            <p>ホーム</p>
          </li>
          <li>
            <img src="../assets/profile.png">
            <p>プロフィール</p>
          </li>
          <li>
            <img src="../assets/logout.png">
            <p>ログアウト</p>
          </li>
        </ul>
      </div>
      <ShareMessage></ShareMessage>
    </div>
</template>

<script>
import ShareMessage from "../components/ShareMessage"
export default {
  components:{
    ShareMessage
  }
}
</script>
<style scoped>
/* 左 */
.menu{
  padding: 20px;
}
.menu-logo{
  width: 100px;
}
.menu-list li{
  display: flex;
  align-items: center;
  margin: 20px 0;
}
.menu-list img{
  display: block;
  width: 30px;
  margin-right: 20px;
}
.menu-list p{
  font-size: 17px;
}
</style>