<template>   
  <!--Login Dialog-->
  <v-card>
    <v-card-title class="grey darken-2">
      Create account
    </v-card-title>
    <v-container>
      <v-row class="mx-2">
        <!--Email field-->
        <v-col cols="12">
          <v-text-field
            v-model="email"
            label="Email"
            prepend-icon="mdi-mail"
          />
        </v-col>
        <!--Password field-->
        <v-col cols="12">
          <v-text-field
            v-model="password"
            prepend-icon="mdi-key"
            :type="show ? 'text' : 'password'"
            name="input-10-1"
            label="Password"
            counter
            @click:append="show = !show"
          ></v-text-field>
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
        @click="login()"
      >Login</v-btn>
      <v-btn
        text
        @click="create=!create"
      >Create
      </v-btn>
    </v-card-actions>

    <!--Create Dialog -->
    <v-dialog
      v-model="create"
      width="800px"
    >
      <createaccount v-on:stopdialog="create = !create" />
    </v-dialog>
  </v-card>
</template>  

<script>
import createaccount from './CreateAccount'

export default {
  name: 'login',
  methods: {
    cancel: function(){
      this.$emit('stopdialog');
    },
    login: function(){
      this.$emit('stopdialog');
      this.$emit('logedin');
    }
  },
  components: {
    createaccount
  },
  data () {
    return {
      create: false,
      show: false,
      create: false,
      password: '',
      email: '',
    }
  }
}
</script>