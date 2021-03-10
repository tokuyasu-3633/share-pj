<template>
  <ul class="home-box">
        <li v-for="(value,index) in shares" :key="index">
          <div class="small-box">
            <p>{{value.name}}</p>
            <img src="../assets/heart.png" @click="fav(index)">
            <p>{{value.like.length}}</p>
            <img src="../assets/cross.png" @click="del(index)" v-if="path && profile">
            <img src="../assets/detail.png" class="return" @click="
              $router.push({
                path: '/detail/' + value.item.id,
                params: {id: value.item.id}
              })
            "
            v-if="profile"
            >
          </div>
          <p>{{value.text}}</p>
        </li>
      </ul>
</template>

<script>
import axios from "axios"
export default {
  data(){
    return{
      shares: [],
      path: true,
      profile: true
    }
  },
  methods: {
    fav(index) {
      const result = this.shares[index].like.some((value) => {
        return value.user_id == this.$store.state.user.id
      })
      if(result) {
        this.shares[index].like.forEach((element) => {
          if (element.user_id == this.$store.state.user.id) {
            axios({
              method: "delete",
              url: "https://evening-eyrie-52589.herokuapp.com/api/like",
              data: {
                share_id: this.shares[index].item.id,
                user_id: this.$store.state.user.id
              }
            }).then((response) => {
              console.log(response);
              this.$router.go({
                path: this.$router.currentRoute.path,
                force: true
              })
            })
          }
        })
      }else{
        axios
          .post("https://evening-eyrie-52589.herokuapp.com/api/like", {
            share_id: this.shares[index].item.id,
            user_id: this.$store.state.user.id,
          })
          .then((response) => {
            console.log(response)
            this.$router.go({
              path: this.$router.currentRoute.path,
              force: true,
            })
          })
      }
    },
    del(index) {
      axios.delete("https://evening-eyrie-52589.herokuapp.com/api/shares/" + this.shares[index].item.id)
      .then((res) => {
        console.log(res)
        this.$router.go({
          path: this.$router.currentRoute.path,
          force: true
          // 意味わからん
        })
      })
    },
    async getShares() {
      let data = []
      const shares = await axios.get("https://evening-eyrie-52589.herokuapp.com/api/shares")
      for(let i = 0;i < shares.data.data.length; i++){
        await axios.get("https://evening-eyrie-52589.herokuapp.com/api/shares/" + shares.data.data[i].id)
        .then((res) => {
          if (this.$route.name == "profile") {
            if (res.data.item.user_id == this.$store.state.user.id){
              data.push(res.data)
            }
          }else if (this.$route.name == "detail"){
            if (res.data.item.id == this.id) {
              data.push(res.data);
            }
          }else{
            data.push(res.data);
          }
        })
      }
      this.shares = data;
      console.log(this.shares);
    }
  },
  created() {
    if (this.$route.name == "home") {
      this.path = false;
    }
    if (this.$route.name == "detail") {
      this.profile = false;
    }
    this.getShares();
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