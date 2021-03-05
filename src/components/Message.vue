<template>
  <ul class="home-box">
        <li v-for="(value,index) in shares" :key="index">
          <div class="small-box">
            <p>{{value.name}}</p>
            <img src="../assets/heart.png">
            <p>{{value.like.length}}</p>
            <img src="../assets/cross.png">
            <img src="../assets/detail.png" class="return">
          </div>
          <p>{{value.text}}</p>
        </li>
      </ul>
</template>

<script>
export default {
  data(){
    return{
      shares: [
        {
          name: "太郎",
          like: [],
          text: "初めまして"
        }
      ]
    }
  }
}
</script>

<style scoped>
.home-box li{
  list-style-type: none;
  height: 117px;
  border: 0.5px solid white;
  border-top: none;
  border-right: none;
  padding: 10px 20px;
}
.small-box{
  display: flex;
}
.small-box img{
  width: 25px;
  margin: 0 10px 10px;
}
.small-box p{
  font-size: 20px;
}
.return{
  margin-left: 20px;
}
</style>