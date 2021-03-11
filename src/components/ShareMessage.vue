<template>
  <div class="share">
        <p>シェア</p>
        <textarea name="text" cols="30" rows="10" id="share-text" v-model="share"></textarea>
        <button @click="send">シェアする</button>
      </div>
</template>

<script>
import axios from "axios";
export default {
  data(){
    return{
      share:"",
    }
  },
  methods: {
    send() {
      if (this.share == ""){
        alert("シェアする内容を入力してください");
      }else{
        axios.post("https://evening-eyrie-52589.herokuapp.com/api/shares", {
          user_id: this.$store.state.user.id,
          share: this.share
        })
        .then((res) => {
          console.log(res);
          alert("シェアしました");
          this.share = "";
          this.$router.go({
            path: this.$router.currentRoute.path,
            force: true,
          })
        })
      }
    }
  }
}
</script>

<style scoped>
.share{
  padding: 20px;
}
#share-text{
  height: 200px;
  width: 350px;
  background: rgb(16, 6, 31);
  border-radius: 10px;
  border: white solid 1px;
  margin: 10px 0;
  color: white;
}
.share button{
  margin-left: 280px;
}
</style>