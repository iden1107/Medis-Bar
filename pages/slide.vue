<template>
  <div class="container">
    <p>slideだ</p>
    <v-text-field
      label="Main input"
      :rules="rules"
      hide-details="auto"
      inputmode="numeric"
    ></v-text-field>
    <v-text-field label="Another input"></v-text-field>
  </div>
</template>


<style scoped lang="scss">
textarea[type="number"]::-webkit-outer-spin-button,
textarea[type="number"]::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
.container {
  max-width: 1100px;
  padding: 8vh 5vh 0vh;
}
img {
  margin: auto;
}
.sub-title{
  font-family: "Cardo";
  font-size: 40px;
  text-align: center;
}
.top {
  background-image: url("~@/assets/restaurant-g691fb34fb_1920.jpg");
  background-size: cover;
  background-position: center center;
  height: 40vh;
  p {
    font-family: "Cardo";
    font-size: 60px;
    line-height: 30vh;
  }
}
</style>
<script>
export default {
  name: "SlidePage",
};
</script>
