<template>
    <div class="slide">
      <div class="container">
        <section>
          <p class="white--text sub-title">slide</p>
        </section>
      </div>
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
.sub-title{
  font-family: "Cardo";
  font-size: 40px;
  text-align: center;
  color: white;
}
</style>
<script>
export default {
  name: "SlidePage",
};
</script>
