<template>
  <v-app dark>
    <v-app-bar :clipped-left="clipped" fixed app color="#364857" dark>
      <v-tabs fixed-tabs centered>
        <v-tab v-scroll-to="'#top'">Top</v-tab>
        <v-tab v-scroll-to="'#about'">About</v-tab>
        <v-menu open-on-hover top offset-y>
          <template v-slot:activator="{ on, attrs }">
            <v-tab v-bind="attrs" v-on="on">Works</v-tab>
          </template>
          <v-list>
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>Sounds</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-title v-scroll-to="'#sounds'"
                >Songs</v-list-item-title
              >
            </v-list-item>
            <v-list-item>
              <v-list-item-title>Applications</v-list-item-title>
            </v-list-item>
            <v-list-item @click="">
              <v-list-item-title>Papers</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
        <v-tab>Skill</v-tab>
      </v-tabs>
    </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer :fixed="fixed" app color="#364857" dark>
      <span>&copy; 2019</span>
    </v-footer>
  </v-app>
</template>
<style scoped></style>
<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: "mdi-apps",
          title: "Welcome",
          to: "/"
        },
        {
          icon: "mdi-chart-bubble",
          title: "Inspire",
          to: "/inspire"
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "Vuetify.js"
    };
  }
};
</script>
