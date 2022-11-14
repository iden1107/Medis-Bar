<template>
  <div class="slide">
    <div class="container">
      <section>
        <p class="sub-title">スライド</p>

        <u>
          <li>違いはmvcとmvvm</li>
          <li>spa</li>
          <li>拡張性の高さ（再利用性）</li>
          <li>DOM操作が楽（コード量の減少）</li>
          <li>双方向バインディング（リアクティブ機能）</li>
          <li>Vueディレクティブ</li>
          <li>フロントエンドに任せろ（v-for）</li>
          <li>デメリット</li>
        </u>

        <p>v-forの内容</p>
        <p></p>
        <p>イヌ</p>
        <p>サル</p>
      </section>
    </div>
  </div>
</template>

<style scoped lang="scss">
.container {
  max-width: 1100px;
  padding: 8vh 5vh 0vh;
}
.sub-title {
  font-size: 40px;
  text-align: center;
}
</style>

<script>
export default {
  name: "SlidePage",
};
</script>
