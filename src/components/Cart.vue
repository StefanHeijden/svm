<template>   
  <v-card>
    <v-card-title class="grey darken-2">
      Shopping Cart
    </v-card-title>
    <v-container>
      <v-row class="mx-2">
        <v-col
          cols="12"
        >
          <v-row
            align="center"
            class="mr-0"
          >
            <v-avatar
              size="40px"
              class="mx-3"
            >
              <img
                src="//ssl.gstatic.com/s2/oz/images/sge/grey_silhouette.png"
                alt=""
              >
            </v-avatar>
            <v-text-field
              v-model="accountname"
              readonly
              placeholder="Not logged in"
              outlined
            />
          </v-row>

          <v-row
            v-for="{name, price} in incart"
            :key="name"
            >
          {{name}}
          <v-spacer></v-spacer>
          <v-divider
            class="mx-4"
            vertical
          ></v-divider>
          {{price}}
          </v-row>

          <v-divider
            horizontal
          ></v-divider>
        </v-col>
      </v-row>
    </v-container>
    <v-card-actions>
      <v-btn
        text
        color="primary"
        @click="cancel()"
      >Cancel</v-btn>
      <v-btn
        text
        @click="buy()"
      >Buy</v-btn>
      <v-btn
        text
        :disabled="loggedin"
        @click="login()"
      >Login</v-btn>
    </v-card-actions>
  </v-card>
</template>  

<script>
import login from './Login'

export default {
  name: 'cart',
  props: ['incart', 'accountname', 'loggedin'],
  components: {
    login
  },
  methods: {
    cancel: function(){
      this.$emit('stopdialog');
    },
    buy: function(){
      this.$emit('stopdialog');
      this.$emit('buy');
    },
    login: function(){
      this.$emit('gotologin');
    },
  },
  data () {
    return {
      startlogin: false,
    }
  }
}
</script>