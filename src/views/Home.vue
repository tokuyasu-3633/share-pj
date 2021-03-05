<template>
  <div class="home">
    <Sidenavi></Sidenavi>
    <div class="right-box">
      <div id="home-title">
        <h1>ホーム</h1>
      </div>
      <Message></Message>
    </div>
  </div>
</template>

<script>
import Sidenavi from "../components/SideNavi"
import Message from '../components/Message.vue'
export default {
  components:{
    Sidenavi,
    Message
  }
}
</script>

<style scoped>
.home{
  background: rgb(16, 6, 31);
  height: 100vh;
  display: flex;
  color: white;
}
/* 右 */
.right-box{
  width: 65%;
}
#home-title{
  font-size: 20px;
  height: 50px;
  width: 100%;
  display: flex;
  align-items: center;
  border: 0.5px solid white;
  border-top: none;
  border-right: none;
  padding: 0 20px;
}
</style>
