<template>
  <v-app id="inspire">


<v-navigation-drawer       v-model="drawer"
      app
      right >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title">
            Application
          </v-list-item-title>
          <v-list-item-subtitle>
            subtext
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        
        dense
        nav
      >
        <v-list-item
        
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>


        <v-app-bar
        app
        color="secundary"
      
      src="https://picsum.photos/1920/1080?random"
      
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>

      <v-spacer></v-spacer>
      <v-toolbar-title>Todo app </v-toolbar-title>

      <v-spacer></v-spacer>
      <!-- PARA MOVER EL BTN SPÑP ES MOVER DE POSICION -->
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>


      <!-- <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn> -->

    </v-app-bar>

    <v-main>
      <!--  -->
      <router-view></router-view>
    </v-main>
  </v-app>
</template>




<script>
  export default {
    data () {
      return {
        drawer: null ,

        items: [
          { title: 'Todo', icon: 'list_alt', to: '/' },
          { title: 'About', icon: 'mdi-help-box', to:'/about' }
        ],
        right: null,
      }
    },
  }
</script>