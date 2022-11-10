<template>
  <div class="order">
    <section class="serch">
      <div class="container">container</div>
    </section>
    <section class="cocktails">
      <div class="container">
        <v-row>
          <div v-for="cocktail in cocktails" :key="cocktail.id">
            <p>{{ cocktail.name }}</p>
            <img :src="require(`@/assets/cocktails/${cocktail.img}.png`)" />
          </div>
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
</style>
<script>
export default {
  name: "OrderPage",
  data() {
    return {
      base: ["Gin", "Vodka", "Rum", "Tequila", "liqueur", "wine","whiskey"],
      cocktails: [
        { id: 1, name: "Mojito", price: 0, base: 2, img: "mojito" },
        { id: 2, name: "Martini", price: 0, base: 0, img: "martini" },
        {id:3,name:"Kir Royal",price:0,base:5,img:"kiri_royal"},
        {id:4,name:"Salty Dog",price:0,base:1,img:"salty_dog"},
        {id:5,name:"Blue Hawaii",price:0,base:2,img:"blue_hawaii"},
        {id:6,name:"Bloody Mary",price:0,base:1,img:"bloody_mary"},
        {id:7,name:"Pink Lady",price:0,base:0,img:"pink_lady"},
        {id:8,name:"Cassis and Orange",price:0,base:4,img:"cassis_orange"},
        {id:9,name:"Grasshopper",price:0,base:4,img:"grasshopper"},
        {id:10,name:"Kahlua and Milk",price:0,base:4,img:"kahlua_and_milk"},
        {id:11,name:"Screwdriver",price:0,base:1,img:"screwdriver"},
        {id:12,name:"Sky Diving",price:0,base:2,img:"sky_diving"},
        {id:13,name:"Spumoni",price:0,base:4,img:"spumoni"},
        {id:14,name:"Balalaika",price:0,base:1,img:"balalaika"},
        {id:15,name:"Margarita",price:0,base:3,img:"margarita"},
        {id:16,name:"Manhattan",price:0,base:6,img:"manhattan"},
        {id:17,name:"Gin and Tonic",price:0,base:0,img:"gin_and_tonic"},
        {id:18,name:"Violet Fizz",price:0,base:4,img:"violet_fizz"},
      ],
    };
  },
  computed: {
    // imgSrc:function (id){
    //   return require("~@/assets/cocktails/" + this.cocktails[id].img + ".png")
    // }
  },
};
</script>
