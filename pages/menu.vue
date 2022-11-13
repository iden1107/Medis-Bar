<template>
  <div class="menu">
    <!-- 検索 -->
    <section class="search">
      <div class="container">

        <p class="white--text">{{filteredCocktails}}</p>
        <p class="white--text">{{searchCondition}}</p>

        <v-row>
          <!-- 名前検索 -->
          <v-col>
            <v-textarea
              v-model="search.name"
              rows="1"
              background-color="white"
              color="black"
              no-resize
            ></v-textarea>
          </v-col>
          <!-- 金額検索（下限・上限） -->
          <v-col>
            <v-textarea
              v-model="search.lowerPrice"
              rows="1"
              background-color="white"
              color="black"
              no-resize>
            </v-textarea>
          </v-col>
          <v-col>
            <v-textarea
              v-model="search.upperPrice"
              rows="1"
              background-color="white"
              color="black"
              no-resize>
            </v-textarea>
          </v-col>
          <!-- ジャンル検索 -->
          <v-col>
            <v-select
              v-model="search.base"
              :items="cocktailbase"
              color="black"
              item-color="black"
              background-color="white"
            ></v-select>
          </v-col>
        </v-row>
      </div>
    </section>

    <!-- メニュー -->
    <section class="cocktails">
      <div class="container">
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
                <p class="font">{{ cocktail.name | firstCharacterUpperCase}}</p>
                <p class="white--text">{{ cocktail.price | locale}}</p>
                <p class="white--text">{{ cocktail.base == 8 ? "ソーダ水":cocktailbase[cocktail.base]}}</p>
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
      name:"abcd ef dd ff",
      cocktailbase: [
        "すべて",
        "ジン",
        "ウォッカ",
        "ラム",
        "テキーラ",
        "リキュール",
        "ワイン",
        "ウィスキー",
      ],
      cocktails: [
        { id: 1, name: "mojito", price: 1500, base: 3, img: "mojito" },
        { id: 2, name: "martini", price:1800, base: 1, img: "martini" },
        { id: 3, name: "kir royal", price: 2300, base: 6, img: "kiri_royal" },
        { id: 4, name: "salty dog", price: 1000, base: 2, img: "salty_dog" },
        { id: 5, name: "blue hawaii", price: 1500, base: 3, img: "blue_hawaii" },
        { id: 6, name: "bloody mary", price: 2800, base: 2, img: "bloody_mary" },
        { id: 7, name: "pink lady", price: 3100, base: 1, img: "pink_lady" },
        {
          id: 8,
          name: "cassis and orange",
          price: 2200,
          base: 5,
          img: "cassis_orange",
        },
        { id: 9, name: "grasshopper", price: 900, base: 5, img: "grasshopper" },
        {
          id: 10,
          name: "kahlua and milk",
          price: 1200,
          base: 5,
          img: "kahlua_and_milk",
        },
        { id: 11, name: "screwdriver", price: 1200, base: 2, img: "screwdriver" },
        { id: 12, name: "sky Diving", price: 1000, base: 3, img: "sky_diving" },
        { id: 13, name: "spumoni", price: 1500, base: 5, img: "spumoni" },
        { id: 14, name: "balalaika", price: 2000, base: 2, img: "balalaika" },
        { id: 15, name: "margarita", price: 2400, base: 4, img: "margarita" },
        { id: 16, name: "manhattan", price: 1100, base: 7, img: "manhattan" },
        {
          id: 17,
          name: "soda",
          price: 10000000,
          base: 8,
          img: "gin_and_tonic",
        },
        { id: 18, name: "Violet Fizz", price: 3000, base: 4, img: "violet_fizz" },
      ],
      // 検索用
      search:{
        name:"",lowerPrice:"",upperPrice:"" , base:"すべて"
      }
    };
  },
  filters:{
    locale(value){
      return  "¥" + value.toLocaleString()
    },
    firstCharacterUpperCase(value){
      // 一旦すべてのメニュー先頭文字を大文字に変更
      let nameString = value.split(' ');
      nameString = nameString.map(result=>result.charAt(0).toUpperCase() + result.slice(1))
      // Andだけすべて小文字にandに変更
      let indexAndString = nameString.indexOf("And")
      nameString[indexAndString] = "and"
      // 文字列をすべて連結し直す
      return nameString.join(" ")
    }
  },
  computed: {
    searchCondition(){
      //
      let copyObjct =  Object.assign({},this.search);
      copyObjct.lowerPrice = copyObjct.lowerPrice == "" ? 0 : copyObjct.lowerPrice
      copyObjct.upperPrice = copyObjct.upperPrice == "" ? Infinity: copyObjct.upperPrice
      return copyObjct
    },
    filteredCocktails(){
      if(this.search.base == "すべて"){
        return this.cocktails.filter((result) =>
          result.name.indexOf(this.search.name) > -1 &&
          result.price >= this.searchCondition.lowerPrice &&
          result.price <= this.searchCondition.upperPrice
        )
      }else{
        // ベース酒を配列のindexに変換
        let selectBase = this.cocktailbase.indexOf(this.search.base)
        // 絞り込み
        return this.cocktails.filter((result) =>
          result.name.indexOf(this.search.name) > -1 &&
          result.price >= this.searchCondition.lowerPrice &&
          result.price <= this.searchCondition.upperPrice &&
          result.base == selectBase
        )
      }
    }
  },

};
</script>
