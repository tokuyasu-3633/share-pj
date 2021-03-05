<template>
  <div class="home">
    <div class="left-box">
      <Sidenavi></Sidenavi>
    </div>
    <div class="right-box">
      <div id="home-title">
        <h1>ホーム</h1>
      </div>
      <Message></Message>
      <div class="comment-box">
        <p>コメント</p>
      </div>
      <div class="comment-in">
        <input type="text" name="comment">
      <button>コメント</button>
      </div>
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
.left-box{
  width: 35%;
}
/* 右 */
.right-box{
  width: 65%;
}
#home-title{
  font-size: 20px;
  height: 50px;
  display: flex;
  align-items: center;
  border: 0.5px solid white;
  border-top: none;
  border-right: none;
  padding: 0 20px;
}
.comment-box{
  height: 50px;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 0.5px solid white;
  border-top: none;
  border-right: none;
}
.comment-in{
text-align: center;
padding: 20px 0;
}
.comment-in input{
  width: 90%;
  height: 30px;
  background: rgb(16, 6, 31);
  border: 0.5px solid white;
  border-radius: 10px;
}
.comment-in button{
  margin: 10px 0 0 87%;
}
</style>
