<template>
  <div>
    <Header></Header>
    <div class="sign">
      <div class="sign-card">
        <form action="" id="sign-form">
          <h1>新規登録</h1>
          <input type="text" name="name" placeholder="ユーザーネーム" v-model="name">
          <input type="text" name="profile" placeholder="プロフィール" v-model="profile">
          <input type="email" name="email" placeholder="メールアドレス" v-model="email">
          <input type="password" name="password" placeholder="パスワード" v-model="password">
          <button @click="auth">ログイン</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "../components/Header"
import axios from "axios"
export default {
  data(){
    return{
      name:"",
      profile:"",
      email:"",
      password:""
    }
  },
  components:{
    Header
  },
  methods: {
    auth(){
      axios
        .post("https://evening-eyrie-52589.herokuapp.com/api/register",{
          name: this.name,
          profile: this.profile,
          email: this.email,
          password: this.password
        })
        .then(response => {
          console.log(response);
          this.$router.replace("/");
        })
        .catch(error => {
          alert(error);
        })
    }
  }
}
</script>

<style scoped>
.sign{
  width: 100%;
  height: calc(100vh - 70px);
  background: rgb(16, 6, 31);
  display: flex;
  justify-content: center;
}
.sign-card{
  background: white;
  width: 380px;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 10px;
  margin-top: 150px;
}

#sign-form input,button{
  display: block;
  margin: 17px auto;
}
#sign-form{
  text-align: center;
}
#sign-form input{
  width: 320px;
  height: 40px;
  border: 1px solid black;
  border-radius: 10px;
  padding-left: 10px;
}
</style>