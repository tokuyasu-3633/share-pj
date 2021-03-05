<template>
  <header>
      <div class="logo-img"><img src="../assets/logo.png" alt=""></div>
      <nav class="header-nav">
        <ul class="header-nav-list">
          <li class="header-nav-item">
            <router-link to="/">ログイン</router-link>
          </li>
          <li class="header-nav-item">
            <router-link to="/signup">新規登録</router-link>
          </li>
        </ul>
      </nav>
  </header>
</template>
<style scoped>
header{
  background: rgb(16, 6, 31);
  height: 70px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 30px;
}
.logo-img{
  width: 150px;
}
.header-nav a{
  color: white;
}
.header-nav-list{
  display: flex;
}
.header-nav-item{
  margin: 0 15px;
}
</style>