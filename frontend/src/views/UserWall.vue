<template>
  <div class="home">
    <div class="header">
      <img
        class="img-groupomania"
        src="../assets/icon-left-font.png"
        alt="logo Groupomania"
      />
      <i
        class="fas fa-user-circle header-profil"
        v-if="!image"
        v-on:click="OpenProfil"
      ></i>
      <img class="img-profil" v-if="image" :src="image" v-on:click="OpenProfil" width="70" height="70" />
    </div>
    <div class="separator"></div>
    <CreatePost />
  </div>
</template>

<script>
import CreatePost from "../components/CreatePost";

export default {
  name: "UserWall",
  components: {
    CreatePost,
  },
  data() {
    return {
      image: localStorage.getItem("imageProfil"),
    };
  },
  methods: {
    OpenProfil() {
      const router = this.$router;
      router.push({ name: "UserProfil" });
    },
  },
};
</script>

<style lang="scss" scoped>
.img-groupomania {
  width: 20%;
  margin-top: 10px;
  margin-left: 20px;
}

.header {
  display: flex;
  justify-content: space-between;
  &-profil {
    margin-top: 15px;
    margin-right: 20px;
    color: #ffd7d7;
    text-decoration: none;
    font-size: 2.5rem;
    cursor: pointer;
  }
}
.separator {
  border: 1px solid rgb(168, 168, 168);
  background-color: rgb(168, 168, 168);
  margin-top: 5px;
}

.img-profil{
  border-radius: 50px;
  margin-top: 5px;
}

@media all and (max-width: 768px) {
  .img-groupomania {
    width: 50%;
  }
}

@media all and (max-width: 450px) {
  .img-groupomania {
    width: 60%;
  }
}
</style>
