<template>
    <div class="slide">
      <div class="container">
        <section>
          <p class="sub-title">スライド</p>
          <p>桃太郎</p>
          <p>イヌ</p>
          <p>サル</p>
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
  font-size: 40px;
  text-align: center;
}
</style>

<script>
export default {
  name: "SlidePage",
};
</script>
