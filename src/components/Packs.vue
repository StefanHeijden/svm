<template>
  <v-container fluid>
    <v-row>
      <v-col cols="12">
        <v-row
          :align="alignment"
          :justify="justify"
          class="grey lighten-5"
          style="height: 100px;"
        >
          <v-card
            v-for="{name, description, type, price} in filter(title, seachstring)"
            :key="name"
            class="ma-3 pa-6"
            outlined
            tile
          >
            <v-card-title class="grey darken-2">
                  {{name}}
            </v-card-title>
            <v-container>
              <v-row class="mx-2">
                <v-col
                  class="align-center justify-space-between"
                  cols="12"
                >
                {{description}}
                </v-col>
                <v-col
                  class="align-center justify-space-between"
                  cols="12"
                >
                {{type}}
                </v-col>
                <v-col
                  class="align-center justify-space-between"
                  cols="12"
                >
                {{price}}
                </v-col>
              </v-row>
            </v-container>
          </v-card>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
let self = this;
export default {
  name: 'packs',
  props: ['title', 'seachstring'], 
  methods: {
    filter: function(title, seachstring){
      var temp = [
        {name: 'pack1', description: 'dummy pack', type: 'liquid', price: '5.00', image: 'assets/logo.png'},
        {name: 'pock2', description: 'dummy pack', type: 'neuro', price: '5.00', image: 'assets/logo.png'}, 
        {name: 'pick3', description: 'dummy pack', type: 'dubstep', price: '15.00', image: 'assets/logo.png'},
        {name: 'puck4', description: 'dummy pack', type: 'dubstep', price: '15.00', image: 'assets/logo.png'}
      ];
      var result = [];
      var n;
      for(n in temp){
        if(title=='packs' || title==temp[n].type){
          if(seachstring.length < 1){
            result.push(temp[n]);
          }else{
            if(temp[n].name.includes(seachstring)){
              result.push(temp[n]);
            }
          }
        }
      }
      return result;
    },
  },
  data () {
    return {
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
