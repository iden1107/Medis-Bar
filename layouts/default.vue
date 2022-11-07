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
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <!-- nav bar -->
    <v-app-bar :clipped-right="clipped" fixed app color="primary">
      <v-toolbar-items class="nav-bar">
        <v-toolbar-title v-text="title" />
        <v-spacer />
        <v-toolbar-items>
          <v-btn text>ORDER</v-btn>
          <v-btn text>CONTACT</v-btn>
        </v-toolbar-items>
        <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      </v-toolbar-items>
    </v-app-bar>

    <!-- main -->
    <v-main>
      <Nuxt />
    </v-main>

    <!-- footer -->
    <v-footer :absolute="!fixed" app color="primary">
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>


<style scoped>
.nav-bar {
  width: 1100px;
  margin: 0 auto;
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
          title: "HOME",
          to: "/",
        },
        {
          icon: "mdi-chart-bubble",
          title: "ORDER",
          to: "/inspire",
        },
        {
          icon: "mdi-chart-bubble",
          title: "CONTACT",
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
