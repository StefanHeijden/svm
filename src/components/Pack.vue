<template>
  <v-card
    outlined
    width="350px"
    color="grey darken-3"
  >
    <v-card-title class="display-1">
      {{name}}
    </v-card-title>
    <v-container>
      <v-row>
        <v-col
          class="align-center justify-space-between"
          cols="12"
        >
        {{description}}
        </v-col>
      </v-row>
    </v-container>
    <v-card-actions>
      <v-chip
        color="red"
        text-color="white"
      >
        <v-avatar left>
          <v-icon>mdi-label</v-icon>
        </v-avatar>
        {{type}}
      </v-chip>
      <v-spacer/>
      <v-chip
        color="indigo"
        text-color="white"
      >
        <v-avatar left>
          <v-icon>mdi-currency-eur</v-icon>
        </v-avatar>
        {{price}}
      </v-chip>
      <v-spacer/>
      <v-btn v-if="!selected" icon color="red" @click="selected=addtocart() ">
        <v-icon>mdi-plus</v-icon>
      </v-btn>
      <v-btn v-if="selected" icon color="red" @click="selected=removefromcart()">
        <v-icon>mdi-checkbox-marked-circle</v-icon>
      </v-btn>
    </v-card-actions>  
  </v-card>
</template>

<script>
export default {
  name: 'pack',
  props: ['id', 'name', 'description', 'type', 'price', 'selected'],
  methods: {
    addtocart: function(){
      this.$emit('addtocart');
      return true;
    },
    removefromcart: function(){
      this.$emit('removefromcart');
      return false;
    },
  },
  data () {
    return {
    }
  },
}
</script>