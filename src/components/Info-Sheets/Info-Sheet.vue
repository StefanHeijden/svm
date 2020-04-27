<template>
  <v-sheet
    color="indigo"
    height="100%"
  >
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
          <div class="display-4">Info</div>
          <v-spacer/>
        </v-row>
      <!--Info-->
        <v-window
          v-model="window"
          class="elevation-1"
          vertical
          height="1200px"
        >
          <v-window-item
          >
            <v-card flat>
              <v-card-text>

                <p class="display-1">
                  info1
                </p>

                <p class="display-1">
                  info2
                </p>

                <p class="display-1">
                  info3
                </p>
                <p class="display-1">
                  info4
                </p>
                <p class="display-1">
                  info5
                </p>
                <p class="display-1">
                  info6
                </p>
              </v-card-text>
            </v-card>
          </v-window-item>
        </v-window>
      <!--Url n stuff-->
        <v-row
          class="mr-0"
        >
        <div class="display-5">URLs</div>
        </v-row>
      </v-col>
    </v-row>
  </v-sheet>
</template>

<script>
export default {
  name: 'infosheet',
  data () {
    return {
    }
  },
}
</script>