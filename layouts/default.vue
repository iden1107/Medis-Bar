<template>
  <v-app>
    <!-- drawer menu -->
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      :disable-resize-watcher="true"
      right
      fixed
      app
      color="red"
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title><p class="white--text drawer-list">{{item.title}}</p></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <!-- nav bar -->
    <v-app-bar :clipped-right="clipped" fixed app color="black">
      <v-toolbar-items class="nav-bar">
        <v-toolbar-title class="white--text d-flex align-center">
          <nuxt-link to="/" tag="p" class="white-text nav-title">{{title}}</nuxt-link>
        </v-toolbar-title>
        <v-spacer />
        <v-toolbar-items>
          <v-btn to="/inspire" text class="white--text" style="text-transform: none">Order</v-btn>
          <v-btn text class="white--text" style="text-transform: none">Contact</v-btn>
          <v-btn  class="primary">スライド</v-btn>
        </v-toolbar-items>
        <v-app-bar-nav-icon @click.stop="drawer = !drawer" class="white--text"/>
      </v-toolbar-items>
    </v-app-bar>

    <!-- main -->
    <v-main>
      <Nuxt />
    </v-main>

    <!-- footer -->
    <v-footer :absolute="!fixed" app color="black">
      <span class="white--text">&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>


<style scoped>
.nav-bar {
  width: 1100px;
  margin: 0 auto;
  font-family: 'Cardo';
}
.nav-title{
  color: white;
  cursor: pointer;
  font-size: 24px;
  margin-bottom: 0;
}
</style>
<script>
export default {
  name: "DefaultLayout",
  data() {
    return {
      clipped: true,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: "mdi-apps",
          title: "Home",
          to: "/",
        },
        {
          icon: "mdi-chart-bubble",
          title: "Order",
          to: "/inspire",
        },
        {
          icon: "mdi-chart-bubble",
          title: "Contact",
          to: "/inspire",
        },
        {
          icon: "mdi-chart-bubble",
          title: "スライド",
          to: "/inspire",
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "Medis Bar",
    };
  },
};
</script>
