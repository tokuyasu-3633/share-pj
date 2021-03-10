<template>
  <div class="home">
    <Sidenavi></Sidenavi>
    <div class="right-box">
      <div id="home-title">
        <h1>プロフィール</h1>
      </div>
      <div class="profile-box">
        <div>
          <h1>{{name}}</h1>
          <p v-if="active">{{profile}}</p>
          <input type="text" v-model="profile" v-else>
        </div>
        <button @click="edit">変更する</button>
      </div>
      <Message></Message>
    </div>
  </div>
</template>

<script>
import Sidenavi from "../components/SideNavi"
import Message from '../components/Message.vue'
import axios from "axios"
export default {
  data(){
    return{
      active: true,
      name: this.$store.state.user.name,
      text: this.$store.state.user.profile
    }
  },
  methods: {
    edit(){
      if (!this.active) {
        axios.put("https://evening-eyrie-52589.herokuapp.com/api/user", {
          email: this.$store.state.user.email,
          profile: this.profile
        })
        .then((res) => {
          this.$store.dispatch("changeUserData", {
            profile: this.profile,
          })
          console.log(res)
        })
      }
      this.active = !this.active;
    }
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
.profile-box{
  display: flex;
  justify-content: space-between;
  padding: 20px;
  border: 0.5px solid white;
  border-top: none;
  border-right: none;
}
.profile-box h1{
  margin-bottom: 10px;
  font-size: 25px;
}
</style>
