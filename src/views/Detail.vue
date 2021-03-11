<template>
  <div class="home">
    <div class="left-box">
      <Sidenavi></Sidenavi>
    </div>
    <div class="right-box">
      <div id="home-title">
        <h1>ホーム</h1>
      </div>
      <Message :id="id"></Message>
      <div>
        <div class="comment-box">
          <p>コメント</p>
        </div>
        <div class="message" v-for="(comment, index) in data" :key="index">
          <div class="flex">
            <p class="name">{{ comment.comment_user.name }}</p>
          </div>
          <div>
            <p class="text">{{ comment.comment.content }}</p>
          </div>
        </div>
        <div class="comment-in" >
          <input type="text" name="comment" v-model="content">
          <button @click="send">コメント</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Sidenavi from "../components/SideNavi"
import Message from '../components/Message.vue'
import axios from 'axios'
export default {
  props: ["id"],
  data() {
    return{
      content: "",
      data: ""
    }
  },
  methods:{
    send() {
      axios.post("https://evening-eyrie-52589.herokuapp.com/api/comment", {
        share_id: this.id,
        user_id: this.$store.state.user.id,
        content: this.content
      })
      .then((res) => {
        console.log(res);
        this.content = ""
        this.$router.go({
          path: this.$router.currentRoute.path,
          force: true
        })
      })
    },
    comment(){
      axios.get("https://evening-eyrie-52589.herokuapp.com/api/shares/" + this.id)
      .then((res) => {
        this.data = res.data.comment;
      })
    }
  },
  created() {
    this.comment()
  },
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
  color: white;
}
.comment-in button{
  margin: 10px 0 0 87%;
}
.share-message {
  border-bottom: 1px solid white;
}
.comment-title {
  text-align: center;
  padding-top: 10px;
  padding-bottom: 10px;
  border-bottom: 1px solid white;
  border-left: 1px solid white;
}
.comment input {
  width: 95%;
  height: 30px;
  margin-top: 20px;
  margin-bottom: 15px;
  margin-left: 10px;
  border-radius: 10px;
  border: 1px solid white;
  background-color: #15202b;
  color: white;
}
.message {
  padding-top: 10px;
  padding-left: 10px;
  padding-bottom: 10px;
  border-bottom: 1px solid white;
  border-left: 1px solid white;
}
</style>
