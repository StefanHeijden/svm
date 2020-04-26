<template>
  <!--Side Bar-->
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      :clipped="$vuetify.breakpoint.lgAndUp"
      app
    >
      <v-list dense>
        <template v-for="item in items">
          <v-list-item
            :key="item.text"
            link
            @click="page = item.click "
          >
            <v-list-item-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>
                {{ item.text }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </template>
      </v-list>
    </v-navigation-drawer>

    <!--Top Bar-->
    <v-app-bar
      :clipped-left="$vuetify.breakpoint.lgAndUp"
      app
      color="blue darken-3"
      dark
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title
        style="width: 300px"
        class="ml-0 pl-4"
      >
        <span class="hidden-sm-and-down">Bruyere</span>
      </v-toolbar-title>
      <v-text-field
        flat
        solo-inverted
        hide-details
        prepend-inner-icon="mdi-magnify"
        label="Search"
        class="hidden-sm-and-down"
      />
      <v-spacer />
      
      <!--ShoppingCart-->
      <v-btn 
        icon
        @click="shop = !shop"
      >
        <v-icon>mdi-cart</v-icon> <!--https://materialdesignicons.com/-->

      <!--Account-->
      </v-btn>
      <v-btn 
        icon
        @click="account = !account"
      >
        <v-icon>mdi-account</v-icon>
      </v-btn>
    </v-app-bar>
    
    <!--Packs-->
    <v-content>
      <packs v-if="page == 'packs'"></packs>
      <info v-if="page == 'info'"></info>
    </v-content>

    <!--ShoppingCart Dialog -->
    <v-dialog
      v-model="shop"
      width="800px"
    >
    <cart/>
    </v-dialog>

    <!--ShoppingCart Dialog -->
    <v-dialog
      v-model="account"
      width="800px"
    >
      <account></account>
    </v-dialog>
  </v-app>
</template>

<script>
import packs from './../src/components/Packs'
import info from './../src/components/Info'
import cart from './../src/components/Cart'
import account from './../src/components/Account'

  export default {
    props: {
      source: String,
    },
    components: {
      packs,
      info,
      cart,
      account
    },
    data: () => ({
      page: 'packs',
      shop: false,
      account: false,
      drawer: null,
      items: [
        { icon: 'mdi-music-note', text: 'Music Packs', click: 'packs'  },
        { text: 'Liquid', click: 'liquid' },
        { text: 'Neuro', click: 'neuro' },
        { text: 'Dubstep', click: 'dubstep' },
        { text: 'Other', click: 'other' },
        { icon: 'mdi-help-circle', text: 'Bruyere', click: 'info' },
        { icon: 'mdi-settings', text: 'Settings' },
      ],
    }),
}
</script>
