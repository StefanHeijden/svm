<template>
  <v-card
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
          cols="4"
        >
          <v-chip
            class="ma-2"
            color="red"
            text-color="white"
          >
            <v-avatar left>
              <v-icon>mdi-label</v-icon>
            </v-avatar>
            {{type}}
          </v-chip>
        </v-col>
        <v-col
          class="align-center justify-space-between"
          cols="6"
        >
          <v-chip
            class="ma-2"
            color="indigo"
            text-color="white"
          >
            <v-avatar left>
              <v-icon>mdi-currency-eur</v-icon>
            </v-avatar>
            {{price}}
          </v-chip>
        </v-col>
        <v-col
          class="align-center justify-space-between"
          cols="2"
        >
        <v-btn v-if="!selected" icon color="red" @click="selected=add(name); ">
          <v-icon>mdi-plus</v-icon>
        </v-btn>
        <v-btn v-if="selected" icon color="red" @click="selected=remove(name)">
          <v-icon>mdi-checkbox-marked-circle</v-icon>
        </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>

<script>
export default {
  name: 'pack',
  props: ['name', 'description', 'type', 'price'],
  methods: {
    add: function(name){
      this.$emit('add', name);
      return true;
    },
    remove: function(name){
      this.$emit('remove', name);
      return false;
    },
  },
  data () {
    return {
      selected: false,
    }
  },
}
</script>