<template>
  <div class="home">
    <section class="title">
      <div class="py-5 mx-auto d-flex align-center justify-center">
        <p class="white--text">Medis Bar</p>
      </div>
    </section>
    <section class="concept">
      <div class="container">
        <p class="white--text text-h4 text-center">concept</p>
        <v-row>
          <v-col cols="12" sm="5">
            <img
              src="~@/assets/alcohol-g119c98c6d_1920.jpg"
              alt=""
              width="100%"
            />
          </v-col>
          <v-col cols="12" sm="7">
            <p class="white--text">
              このサイトはVueの紹介サイトです。本サイトはフィクションであり、実在する人物、団体等とは一切関係ありません。<br />
              このサイトはVueの紹介サイトです。本サイトはフィクションであり、実在する人物、団体等とは一切関係ありません。<br />
              このサイトはVueの紹介サイトです。本サイトはフィクションであり、実在する人物、団体等とは一切関係ありません。<br />
            </p>
          </v-col>
        </v-row>
      </div>
    </section>
    <section class="store">
      <div class="container">
        <p class="white--text text-h4 text-center">store</p>
        <v-row>
          <v-col cols="12" sm="6">
            <p class="white--text text-center text-h5">新宿店</p>
            <img
              src="~@/assets/bar-g652964793_1920.jpg"
              alt=""
              width="100%"
            />
          </v-col>
          <v-col cols="12" sm="6">
            <p class="white--text text-center text-h5">渋谷店</p>
            <img
              src="~@/assets/bar-g53473698e_1920.jpg"
              alt=""
              width="100%"
            />
          </v-col>
        </v-row>
      </div>
    </section>
  </div>
</template>


<style scoped lang="scss">
.container {
  max-width: 1100px;
  padding: 5vh 5vh 0vh;
}
img {
  margin: auto;
}
.home {
  background-image: url("~@/assets/black-g73bfa2a23_1280.png");
  background-size: cover;
  background-attachment: fixed;
  height: 100%;
}
.title {
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
  name: "IndexPage",
};
</script>
