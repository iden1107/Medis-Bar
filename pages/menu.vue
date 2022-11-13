<template>
  <div class="menu">
    <!-- 検索 -->
    <section class="serch">
      <div class="container">
        <p>{{serch.base}}</p>
        <v-combobox
          v-model="serch.base"
          :items="cocktailbase.id"
          label="ジャンル"
        ></v-combobox>
      </div>
    </section>
    <!-- メニュー -->
    <section class="cocktails">
      <div class="container">
        <p class="white--text">{{cocktailbase[3]}}</p>
        <v-row>
          <v-col
            cols="12"
            md="6"
            v-for="cocktail in filteredCocktails"
            :key="cocktail.id"
            class="d-flex"
          >
              <img
                :src="require(`@/assets/cocktails/${cocktail.img}.png`)"
              />
              <div class="detail">
                <p class="font">{{ cocktail.name }}</p>
                <p class="white--text">{{ cocktail.price | locale}}</p>
                <p class="white--text">{{ cocktail.base}}</p>
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
      cocktailbase: [
        {id:1,categories:"ジン",},
        {id:2,categories:"ウォッカ"},
        {id:3,categories:"ラム"},
        {id:4,categories:"テキーラ"},
        {id:5,categories:"リキュール"},
        {id:6,categories:"ワイン"},
        {id:7,categories:"ウィスキー"},
      ],
      cocktails: [
        { id: 1, name: "Mojito", price: 1500, base: 3, img: "mojito" },
        { id: 2, name: "Martini", price:1800, base: 1, img: "martini" },
        { id: 3, name: "Kir Royal", price: 2300, base: 6, img: "kiri_royal" },
        { id: 4, name: "Salty Dog", price: 1000, base: 2, img: "salty_dog" },
        { id: 5, name: "Blue Hawaii", price: 1500, base: 3, img: "blue_hawaii" },
        { id: 6, name: "Bloody Mary", price: 2800, base: 2, img: "bloody_mary" },
        { id: 7, name: "Pink Lady", price: 3100, base: 1, img: "pink_lady" },
        {
          id: 8,
          name: "Cassis and Orange",
          price: 2200,
          base: 5,
          img: "cassis_orange",
        },
        { id: 9, name: "Grasshopper", price: 900, base: 5, img: "grasshopper" },
        {
          id: 10,
          name: "Kahlua and Milk",
          price: 1200,
          base: 5,
          img: "kahlua_and_milk",
        },
        { id: 11, name: "Screwdriver", price: 1200, base: 2, img: "screwdriver" },
        { id: 12, name: "Sky Diving", price: 1000, base: 3, img: "sky_diving" },
        { id: 13, name: "Spumoni", price: 1500, base: 5, img: "spumoni" },
        { id: 14, name: "Balalaika", price: 2000, base: 2, img: "balalaika" },
        { id: 15, name: "Margarita", price: 2400, base: 4, img: "margarita" },
        { id: 16, name: "Manhattan", price: 1100, base: 7, img: "manhattan" },
        {
          id: 17,
          name: "Soda",
          price: 10000000,
          base: "",
          img: "gin_and_tonic",
        },
        { id: 18, name: "Violet Fizz", price: 3000, base: 5, img: "violet_fizz" },
      ],
      serch:{
        base:1
      }
    };
  },
  filters:{
    locale(value){
      return  "¥" + value.toLocaleString()
    }
  },
  computed: {
    filteredCocktails(){
      let x = this.cocktails
      console.log(x)
      return x
    }
  },
};
</script>
