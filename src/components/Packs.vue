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
            v-for="{id, name, description, type, price} in filter(title, seachstring)"
            :key="name"
            v-bind:id="id"
            v-bind:name="name"
            v-bind:description="description"
            v-bind:type="type"
            v-bind:price="price"
            v-bind:selected="selected"
            v-on:addtocart="addtocart({id, name, description, type, price})"
            v-on:removefromcart="removefromcart({id, name, description, type, price})"
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
  props: ['title', 'seachstring', 'incart'], 
  components: {
    pack
  },
  methods: {
    filter: function(title, seachstring){
      var temp = [
        {id: 0, name: 'pack1', description: 'dummy pack', type: 'liquid', price: 5.00, selected: 'false'},
        {id: 1, name: 'pock2', description: 'dummy pack', type: 'neuro', price: 5.00, selected: 'false'}, 
        {id: 2, name: 'pick3', description: 'dummy pack', type: 'dubstep', price: 15.00, selected: 'false'},
        {id: 3, name: 'puck4', description: 'dummy pack', type: 'dubstep', price: 15.00, selected: 'false'}
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
    addtocart: function(pack){
      var has = false;
      for (var i = 0; i < this.incart.length; i++) {
        if(pack.id == this.incart[i].id){// this doesn't work, why???
          has = true;
        }
      }
      if(!has){
        this.incart.push(pack);
      }
    },
    removefromcart: function(pack){
      if(this.incart.length > 0){
        var index = -1;
        for (var i = 0; i < this.incart.length; i++) {
          if(pack.id == this.incart[i].id){// this doesn't work, why???
            index = i;
          }
        }
        if(index >= 0){
          this.incart.splice(index, 1);
        }
      }
    },
  },
  data () {
    return {
    }
  }
}
</script>

