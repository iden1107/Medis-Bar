<template>
  <div class="contact">
    <div class="container">
      <section>
        <p class="white--text sub-title">Contact</p>
        <v-text-field
          label="Main input"
          :rules="rules"
          hide-details="auto"
          inputmode="numeric"
        ></v-text-field>
        <v-text-field label="Another input"></v-text-field>
      </section>
    </div>
  </div>
</template>

<style scoped lang="scss">
.container {
  max-width: 1100px;
  padding: 8vh 5vh 0vh;
}
.sub-title{
  font-family: "Cardo";
  font-size: 40px;
  text-align: center;
}
</style>

<script>
export default {
  name: "ContactPage",
};
</script>
