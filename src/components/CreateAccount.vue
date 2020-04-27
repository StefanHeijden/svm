<template>   
  <!--Create Account Dialog-->
  <v-card>
    <v-card-title class="grey darken-2">
      Create account
    </v-card-title>
    <v-container>
      <v-row class="mx-2">
        <!--Name field-->
        <v-col cols="12">
          <v-text-field
            v-model="name"
            label="Name"
            prepend-icon="mdi-account"
            :rules="[rules.required]"
          />
        </v-col>
        <!--Password field-->
        <v-col cols="12">
          <v-text-field
            v-model="password"
            prepend-icon="mdi-key"
            :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
            :rules="[rules.required, rules.min]"
            :type="show ? 'text' : 'password'"
            name="input-10-1"
            label="Password"
            hint="At least 8 characters, 1 number and 1 sign."
            counter
            @click:append="show = !show"
          ></v-text-field>
        </v-col>
        <!--Email field-->
        <v-col cols="12">
          <v-text-field
            v-model="email"
            label="Email"
            prepend-icon="mdi-mail"
            :rules="[rules.required, rules.mail]"
          />
        </v-col>
        <!--Phone field-->
        <v-col cols="12">
          <v-text-field
            v-model="phone"
            type="tel"
            prepend-icon="mdi-phone"
            placeholder="(000) 000 - 0000"
            :rules="[rules.phone]"
          />
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
        @click="create()"
      >Create</v-btn>
    </v-card-actions>
  </v-card>
</template>  

<script>
export default {
  name: 'createaccount',
  methods: {
    cancel: function(){this.$emit('stopdialog')
    },
    create: function(){this.$emit('stopdialog')
    },
    checknumber: function(value){
      if(value.length < 1){
        return true;
      }
      var numbers = /^[0-9]+$/;
      if(value.value.match(numbers))
      {
      return true;
      }
      else
      {
      return false;
      }
    }
  },
  data () {
    return {
      show: false,
      name: '',
      password: '',
      email: '',
      phone: '',
      rules: {
        required: value => !!value || 'Required.',
        min: v => v.length >= 8 || 'Min 8 characters',
        mail: email => email.includes('@') || 'Must be valid email',
        phone: phone => this.checknumber(phone) || 'Must be valid phonenumber',
      },
    }
  }
}
</script>