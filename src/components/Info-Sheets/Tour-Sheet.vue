<template>
  <v-sheet
    color="red lighten-1"
    height="100%"
  >
  <!--Titel-->
    <v-row class="mx-2">
      <v-col
        cols="12"
      >
      <!--Titel-->
        <v-row
          align="center"
          class="mr-0"
        >
          <v-spacer/>
            <div class="display-4">Tours</div>
          <v-spacer/>
        </v-row>
        <v-row
          align="center"
          class="mr-0"
        >
          <v-spacer/>
            <div class="display-3">No tours so far :(</div>
          <v-spacer/>
        </v-row>
      </v-col>
    </v-row>
  </v-sheet>
</template>

<script>
export default {
  name: 'toursheet',
  data () {
    return {
    }
  },
}
</script>