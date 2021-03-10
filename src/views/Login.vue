<template>
  <div>
    <Header></Header>
    <div class="login">
      <div class="login-card">
        <form action="" id="login-form">
          <h1>ログイン</h1>
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
export default {
  data(){
    return{
      email: "",
      password: ""
    }
  },
  components:{
    Header
  },
  methods: {
    auth() {
      this.$store.dispatch("login", {
        email: this.email,
        password: this.password
      })
    }
  }
}
</script>

<style scoped>
.login{
  width: 100%;
  height: calc(100vh - 70px);
  background: rgb(16, 6, 31);
  display: flex;
  justify-content: center;
}
.login-card{
  background: white;
  width: 380px;
  height: 240px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 10px;
  margin-top: 150px;
}

#login-form input,button{
  display: block;
  margin: 15px auto;
}
#login-form{
  text-align: center;
}
#login-form input{
  width: 320px;
  height: 40px;
  border: 1px solid black;
  border-radius: 10px;
  padding-left: 10px;
}
</style>

