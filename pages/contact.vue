<template>
  <div class="contact">
    <div class="container">
      <section>
        <p class="white--text sub-title">Contact</p>
        <p>お名前<span v-show="inquiryForm.name == ''? true: false" class="error--text">  必須項目です</span></p>
        <v-text-field
          @blur="blurText('name')"
          v-model="inquiryForm.name"
          rows="1"
          background-color="white"
          color="black"
          no-resize>
        ></v-text-field>
        <p>フリガナ<span v-show="inquiryForm.kana == ''? true: false" class="error--text">  必須項目です</span></p>
        <v-text-field
          @blur="blurText('kana')"
          v-model="inquiryForm.kana"
          rows="1"
          background-color="white"
          color="black"
          no-resize>
        ></v-text-field>
        <p>メールアドレス<span v-show="inquiryForm.email == ''? true: false" class="error--text">  必須項目です</span></p>
        <v-text-field
          @blur="blurText('email')"
          v-model="inquiryForm.email"
          rows="1"
          background-color="white"
          color="black"
          no-resize>
        ></v-text-field>
        <p>お問い合わせ内容<span v-show="inquiryForm.content == ''? true: false" class="error--text">  必須項目です</span></p>
        <v-textarea
          @blur="blurText('content')"
          v-model="inquiryForm.content"
          background-color="white"
          color="black">
        ></v-textarea>
        <nuxt-link to="/"><button :disabled="buttonDisable">送信</button></nuxt-link>
        <span class="white--text">※実際には送信されません</span>
      </section>
    </div>
  </div>
</template>

<style scoped lang="scss">
.contact{
  background-image: url("~@/assets/black-g73bfa2a23_1280.png");
  background-size: cover;
  background-attachment: fixed;
  height: 100%;
  p{
    margin: 0;
    color: white;
  }
  .v-text-field{
    padding: 0;
  }
}
button{
  padding: 5px 15px;
  border-radius: 3px;
  background-color: white;
  color: black;
  &:disabled{
    background-color: gray;
    opacity: 0.8;
  }
}
.container {
  max-width: 1100px;
  padding: 0vh 5vh 5vh;
}
.sub-title{
  font-family: "Cardo";
  font-size: 40px;
  text-align: center;
  padding-top: 5vh;
}
</style>

<script>
export default {
  name: "ContactPage",
  data(){
    return{
      inquiryForm:{
        name:null,kana:null,email:null,content:null
      }
    }
  },
  methods:{
    // 空文字だったらエラーを表示するメソッド
    blurText(value){
      if(this.inquiryForm[value] == null){
        this.inquiryForm[value] = ""
      }
    }
  },
  computed:{
    buttonDisable(){
      if(!this.inquiryForm.name || !this.inquiryForm.kana  || !this.inquiryForm.email || !this.inquiryForm.content){
        return true
      }else{
        return false
      }
    }
  }
};
</script>
