<template>
  <div class="menu">
    <p class="white--text sub-title">Menu</p>
    <!-- 検索バー -->
    <section class="search">
      <div class="container">
        <v-row class="search-bar">
          <!-- 名前検索 -->
          <v-col cols="6" md="3">
            <p>カクテル名</p>
            <v-text-field
              label=""
              v-model="search.name"
              rows="1"
              background-color="white"
              color="black"
              no-resize
            ></v-text-field>
          </v-col>
          <!-- ジャンル検索 -->
          <v-col cols="6" md="3">
            <p>ジャンル</p>
            <v-select
              v-model="search.base"
              :items="cocktailbase"
              color="black"
              item-color="black"
              background-color="white"
              class="p-0"
            ></v-select>
          </v-col>
          <!-- 金額検索（下限） -->
          <v-col cols="6" md="3">
            <p>下限価格</p>
            <v-text-field
              v-model.number="search.lowerPrice"
              type="number"
              hide-spin-buttons
              placeholder="MIN"
              background-color="white"
              color="black"
              no-resize>
            </v-text-field>
          </v-col>
          <!-- 金額検索（上限） -->
          <v-col cols="6" md="3">
            <p>上限価格</p>
            <v-text-field
              v-model.number="search.upperPrice"
              type="number"
              hide-spin-buttons
              placeholder="MAX"
              background-color="white"
              color="black"
              no-resize>
            </v-text-field>
          </v-col>
          <!-- クリアボタン -->
          <v-col cols="12"  class="d-flex justify-end">
            <v-btn color="white" @click="searchClear" >クリア</v-btn>
          </v-col>
        </v-row>
      </div>
    </section>

    <!-- メニュー -->
    <section class="cocktails">
      <div class="container">
        <transition-group name="menu" tag="v-row" class="row">
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
        </transition-group>
      </div>
    </section>
  </div>
</template>

<style lang="scss" scoped>
.menu{
  background-image: url("~@/assets/black-g73bfa2a23_1280.png");
  background-size: cover;
  background-attachment: fixed;
  height: 100%;
}
.search{
  display: fixed;
}
.container {
  max-width: 1100px;
  padding: 0 5vh 5vh;
  p{
    margin: 10px 0 0;
    color: white;
  }
  .v-select,.v-text-field{
    padding-top: 0;
  }
}
img{
  width: 45%;
  max-width: 250px;
}
.sub-title{
  font-family: "Cardo";
  font-size: 40px;
  text-align: center;
  padding-top:5vh;
}
.col-6{
  padding: 0 2vh;
}
.detail{
  padding: 0 16px;
}
.font{
  font-family: 'Cardo';
  color: white;
  font-size: 22px;
}
// アニメーション
.menu-enter-active, .menu-leave-active, .menu-move {
  transition: opacity 1s, transform 1s;
}
.menu-leave-active {
  position: absolute;
}
.menu-enter {
  opacity: 0;
  transform: translateX(-100px);
}
.menu-leave-to {
  opacity: 0;
  transform: translateX(100px);
}
</style>

<script>
export default {
  name: "MenuPage",
  data() {
    return {
      cocktailbase: ["すべて","ジン","ウォッカ","ラム","テキーラ","リキュール","ワイン","ウィスキー"],
      cocktails: [
        { id: 1, name: "mojito", price: 1500, base: 3, img: "mojito" },
        { id: 2, name: "martini", price:1800, base: 1, img: "martini" },
        { id: 3, name: "kir royal", price: 2300, base: 6, img: "kiri_royal" },
        { id: 4, name: "salty dog", price: 1000, base: 2, img: "salty_dog" },
        { id: 5, name: "blue hawaii", price: 1500, base: 3, img: "blue_hawaii" },
        { id: 6, name: "bloody mary", price: 2800, base: 2, img: "bloody_mary" },
        { id: 7, name: "pink lady", price: 3100, base: 1, img: "pink_lady" },
        { id: 8,name: "cassis and orange",price: 2200,base: 5,img: "cassis_orange",},
        { id: 9, name: "grasshopper", price: 900, base: 5, img: "grasshopper" },
        { id: 10,name: "kahlua and milk",price: 1200,base: 5,img: "kahlua_and_milk",},
        { id: 11, name: "screwdriver", price: 1200, base: 2, img: "screwdriver" },
        { id: 12, name: "sky Diving", price: 1000, base: 3, img: "sky_diving" },
        { id: 13, name: "spumoni", price: 1500, base: 5, img: "spumoni" },
        { id: 14, name: "balalaika", price: 2000, base: 2, img: "balalaika" },
        { id: 15, name: "margarita", price: 2400, base: 4, img: "margarita" },
        { id: 16, name: "manhattan", price: 1100, base: 7, img: "manhattan" },
        { id: 17,name: "soda",price: 1000000,base: 8,img: "gin_and_tonic",},
        { id: 18, name: "Violet Fizz", price: 3000, base: 4, img: "violet_fizz" },
      ],
      // 検索用デフォルト値
      search:{
        name:"",lowerPrice:"",upperPrice:"" , base:"すべて"
      }
    };
  },
  methods:{
    // 検索窓クリアメソッド（デフォルト値に戻す）
    searchClear(){
      this.search = {
        name:"",lowerPrice:"",upperPrice:"" , base:"すべて"
      }
    }
  },
  filters:{
    locale(value){
      return "¥" + value.toLocaleString()
    },
    firstCharacterUpperCase(value){
      // メニュー文字の文字変換
      // 一旦すべてのメニュー先頭文字を大文字に変更
      let nameString = value.split(' ');
      nameString = nameString.map(result=>result.charAt(0).toUpperCase() + result.slice(1))
      // Andだけすべて小文字にandに変更
      let indexAndString = nameString.indexOf("And")
      nameString[indexAndString] = "and"
      // 文字列を再連結
      return nameString.join(" ")
    }
  },
  computed: {
    condition(){
      // 検索条件用オブジェクト
      let copyObject = Object.assign({}, this.search)
      // 検索の上限・下限の値を0と無限大に入れ直す
      copyObject.lowerPrice = copyObject.lowerPrice == "" ? 0: copyObject.lowerPrice
      copyObject.upperPrice = copyObject.upperPrice == "" ? Infinity: copyObject.upperPrice
      return copyObject
    },
    filteredCocktails(){
      // 描画するカクテルの抽出（検索条件用オブジェクトを参照する）
      // ジャンルの有無で条件分岐
      if(this.condition.base == "すべて"){
        return this.cocktails.filter((result) =>
          result.name.indexOf(this.condition.name) > -1 &&
          result.price >= this.condition.lowerPrice &&
          result.price <= this.condition.upperPrice
        )
      }else{
        // 選択されたジャンルを配列のindexに割り当てて変換
        let selectBase = this.cocktailbase.indexOf(this.condition.base)
        // 合致するジャンルの絞り込み
        return this.cocktails.filter((result) =>
          result.name.indexOf(this.condition.name) > -1 &&
          result.price >= this.condition.lowerPrice &&
          result.price <= this.condition.upperPrice &&
          result.base == selectBase
        )
      }
    }
  },
};
</script>
