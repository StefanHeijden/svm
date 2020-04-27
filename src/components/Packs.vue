<template>
  <v-container fluid>
    <v-row>
      <v-col cols="12">
        <v-row
          :align="alignment"
          :justify="justify"
          class="grey lighten-5"
        >
          <pack
            v-for="{name, description, type, price} in filter(title, seachstring)"
            :key="name"
            v-bind:name="name"
            v-bind:description="description"
            v-bind:type="type"
            v-bind:price="price"
            class="ma-3 pa-6"
          />
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import pack from './Pack'

export default {
  name: 'packs',
  props: ['title', 'seachstring'], 
  components: {
    pack
  },
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
    add: function(name){
      this.$emit('add', name);
    },
  },
  data () {
    return {
    }
  }
}
</script>

