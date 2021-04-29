<template>
  <v-app dark>
    <!--    left navigation -->
    <!--    <v-navigation-drawer-->
    <!--      v-model="drawer"-->
    <!--      :mini-variant="miniVariant"-->
    <!--      :clipped="clipped"-->
    <!--      fixed-->
    <!--      app-->
    <!--    >-->
    <!--      <v-list>-->
    <!--        <v-list-item-->
    <!--          v-for="(item, i) in items"-->
    <!--          :key="i"-->
    <!--          :to="item.to"-->
    <!--          router-->
    <!--          exact-->
    <!--        >-->
    <!--          <v-list-item-action>-->
    <!--            <v-icon>{{ item.icon }}</v-icon>-->
    <!--          </v-list-item-action>-->
    <!--          <v-list-item-content>-->
    <!--            <v-list-item-title v-text="item.title"/>-->
    <!--          </v-list-item-content>-->
    <!--        </v-list-item>-->
    <!--      </v-list>-->
    <!--    </v-navigation-drawer>-->
    <!--  header navbar -->
    <v-app-bar
      :clipped-left="clipped"
      :clipped-right="rightClipped"
      class="header-nav"
      fixed
      app
    >
      <!--      <v-app-bar-nav-icon @click.stop="drawer = !drawer" class="color-white"/>-->
      <!--      <v-btn-->
      <!--        icon-->
      <!--        @click.stop="clipped = !clipped"-->
      <!--      >-->
      <!--        <v-icon class="color-white application-icon">mdi-application</v-icon>-->
      <!--      </v-btn>-->
      <v-row>
        <v-col md="8" offset-md="2">
          <div class="d-flex align-center">
            <v-toolbar-title v-text="title" class="color-white"/>
            <v-spacer></v-spacer>
            <v-tooltip bottom>
              <template v-slot:activator="{ on, attrs }">
                <v-btn
                  v-bind="attrs"
                  v-on="on"
                  @click="rightDrawer = true"
                  icon
                >
                  <v-icon color="#fff">
                    mdi-trophy-variant-outline
                  </v-icon>
                </v-btn>
              </template>
              <span>Spreadsheet</span>
            </v-tooltip>
          </div>
        </v-col>
      </v-row>
      <!--      <v-spacer></v-spacer>-->
      <!--    -->
      <!--      <v-spacer></v-spacer>-->
      <!--
           <span-->
      <!--        class="advertising"-->
      <!--        @click.stop="rightDrawer = !rightDrawer"-->
      <!--      >-->
      <!--        <span>advertising</span>-->
      <!--      </span>-->
    </v-app-bar>
    <!--   main part  -->
    <v-main>
      <v-row class="py-2">
        <v-col offset-md="2" md="8">
          <v-row>
            <v-col cols="12" md="9" sm="8">
              <v-card outlined class="px-5 py-5">
                <nuxt/>
              </v-card>
            </v-col>
            <v-col cols="12" md="3" sm="3">
              <v-card outlined>
                card
              </v-card>

            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-main>
    <!--        right navigation-->
    <v-navigation-drawer
      v-model="rightDrawer"
      :clipped="rightClipped"
      style=" background-color: #35495e"
      width="400"
      right
      fixed

    >
      <v-btn icon @click="rightDrawer = false" class="ml-5 mt-5 closeButton">
        <v-icon>
          mdi-close
        </v-icon>
      </v-btn>
      <h4 class="text-center py-5 mt-5" style="background-color: #35495e">Users Rating Dashboard</h4>
      <hr>
      <v-text-field outlined dense class="mt-2 mx-2" label="search user" color="dark"></v-text-field>
      <v-data-table
        :headers="headers"
        :items="tableItems"
        :items-per-page="5"
        class="elevation-1 mx-2"
      >
      </v-data-table>
    </v-navigation-drawer>
    <v-footer
      :absolute="!fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: true,
      drawer: false,
      fixed: false,
      rightClipped: false,
      headers: [
        {text: "№", value: "number"},
        {text: "Name", value: "name"},
        {text: "Rate", value: "rate"},
      ],
      tableItems: [
        {number: 1, name: "Asilbek", rate: 100},
        {number: 2, name: "Ahror", rate: 90},
      ],
      items: [
        {
          icon: 'mdi-apps',
          title: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: true,
      title: 'StackUz'
    }
  },
  methods: {
    rightDrawerClick() {
      alert('message')
    }
  }
}
</script>
<style scoped>
@media (max-width: 1264px) {
  .application-icon {
    display: none;
  }
}

.closeButton {
  background-color: #35495e;
  cursor: pointer;
  font-size: 30px !important;
}

.advertising {
  background-color: black;
  color: white;
  padding: 5px;
  cursor: pointer;
}

.header-nav {
  background-color: black !important;
}

.color-white {
  color: white !important;
}
</style>
