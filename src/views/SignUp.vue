<template>
  <div>
    <Header></Header>
    <div class="sign">
      <div class="sign-card">
        <form action="" id="sign-form">
          <h1>新規登録</h1>
          <input type="text" name="name" placeholder="ユーザーネーム">
          <input type="text" name="profile" placeholder="プロフィール">
          <input type="email" name="email" placeholder="メールアドレス">
          <input type="password" name="password" placeholder="パスワード">
          <button>ログイン</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "../components/Header"
export default {
  components:{
    Header
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