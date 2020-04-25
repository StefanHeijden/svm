<template>
  <v-container fluid>
    <v-row>
      <v-col cols="12">
        <v-row
          :align="alignment"
          :justify="justify"
          class="grey lighten-5"
          style="height: 300px;"
        >
          <v-card
            v-for="n in 3"
            :key="n"
            class="ma-3 pa-6"
            outlined
            tile
          >
            Column
          </v-card>
        </v-row>
      </v-col>
      <v-col cols="12">
        <v-row justify="center">
          <v-col
            cols="6"
            md="2"
          >
            <v-select
              v-model="alignment"
              :items="alignmentsAvailable"
              label="Align"
            ></v-select>
          </v-col>

          <v-col
            cols="6"
            md="2"
          >
            <v-select
              v-model="justify"
              :items="justifyAvailable"
              label="Justify"
            ></v-select>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      cards: [
      {name: 'pack1', description: 'dummy pack', price: '5.00', image: 'assets/logo.png'},
      {name: 'pack2', description: 'dummy pack', price: '5.00', image: 'assets/logo.png'}, 
      {name: 'pack3', description: 'dummy pack', price: '15.00', image: 'assets/logo.png'}
    ]
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
