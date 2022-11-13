<template>
  <div class="menu">
    <section class="serch">
      <div class="container">container</div>
    </section>
    <section class="cocktails">
      <div class="container">
        <button @click="judgeCocktailBase(0)">button</button>
        <v-row>
          <v-col
            cols="12"
            md="6"
            v-for="cocktail in cocktails"
            :key="cocktail.id"
            class="d-flex"
          >

              <img
                :src="require(`@/assets/cocktails/${cocktail.img}.png`)"
              />
              <div class="detail">
                <p class="font">{{ cocktail.name }}</p>
                <p class="white--text">{{ cocktail.price | locale}}</p>
                <p class="white--text">{{ cocktailbase[cocktail.base] }}</p>
              </div>

          </v-col>

        </v-row>
      </div>
    </section>
  </div>
</template>

<style lang="scss" scoped>
.container {
  max-width: 1100px;
  padding: 5vh;
}
img{
  width: 45%;
  max-width: 250px;
}
.detail{
  padding: 0 16px;
}
.font{
  font-family: 'Cardo';
  color: white;
  font-size: 22px;
}
</style>
<script>
export default {
  name: "MenuPage",
  data() {
    return {
      cocktailbase: ["ジン", "ウォッカ", "ラム", "テキーラ", "リキュール", "ワイン", "ウィスキー","ただのソーダ水"],
      cocktails: [
        { id: 1, name: "Mojito", price: 1500, base: 2, img: "mojito" },
        { id: 2, name: "Martini", price:1800, base: 0, img: "martini" },
        { id: 3, name: "Kir Royal", price: 2300, base: 5, img: "kiri_royal" },
        { id: 4, name: "Salty Dog", price: 1000, base: 1, img: "salty_dog" },
        { id: 5, name: "Blue Hawaii", price: 1500, base: 2, img: "blue_hawaii" },
        { id: 6, name: "Bloody Mary", price: 2800, base: 1, img: "bloody_mary" },
        { id: 7, name: "Pink Lady", price: 3100, base: 0, img: "pink_lady" },
        {
          id: 8,
          name: "Cassis and Orange",
          price: 2200,
          base: 4,
          img: "cassis_orange",
        },
        { id: 9, name: "Grasshopper", price: 900, base: 4, img: "grasshopper" },
        {
          id: 10,
          name: "Kahlua and Milk",
          price: 1200,
          base: 4,
          img: "kahlua_and_milk",
        },
        { id: 11, name: "Screwdriver", price: 1200, base: 1, img: "screwdriver" },
        { id: 12, name: "Sky Diving", price: 1000, base: 2, img: "sky_diving" },
        { id: 13, name: "Spumoni", price: 1500, base: 4, img: "spumoni" },
        { id: 14, name: "Balalaika", price: 2000, base: 1, img: "balalaika" },
        { id: 15, name: "Margarita", price: 2400, base: 3, img: "margarita" },
        { id: 16, name: "Manhattan", price: 1100, base: 6, img: "manhattan" },
        {
          id: 17,
          name: "Soda",
          price: 10000000,
          base: 7,
          img: "gin_and_tonic",
        },
        { id: 18, name: "Violet Fizz", price: 3000, base: 4, img: "violet_fizz" },
      ],
    };
  },
  filters:{
    locale(value){
      return  "¥" + value.toLocaleString()
    }
  }
  // computed: {
  //   judgeCocktailBase:function (id){
  //     return this.base(id)
  //   }
  // },
};
</script>
