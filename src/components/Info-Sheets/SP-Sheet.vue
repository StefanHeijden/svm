<template>
  <v-sheet
    color="green darken-4"
    height="100%"
  >
  <!--Titel-->
    <v-row>
      <v-col cols="12" >
        <v-card>
          <v-container fluid>
            <v-row>
              <v-col
                v-for="{name, image, url} in albums"
                :key="name"
                class="d-flex child-flex"
                cols="4"
              >
                <v-card flat tile class="d-flex">
                  <v-img
                    :src="image"
                     v-on:click="select(url)"
                    aspect-ratio="1"
                    class="grey lighten-2"
                  >
                    <template>
                      <v-row
                        class="fill-height ma-0"
                        align="center"
                        justify="center"
                      >
                      <div class="display-3" >{{name}}</div>
                      </v-row>
                    </template>
                  </v-img>
                </v-card>
              </v-col>
            </v-row>
          </v-container>
        </v-card>
      </v-col>
    </v-row>
  </v-sheet>
</template>

<script>
import image from "./../../assets/Observers.png"

export default {
  name: 'spsheet',
  methods: {
    select: function(url) {
      window.location.href = url;
    }
  },
  data () {
    return {
      albums: [
        {name: "Observers", image: image, url: "https://open.spotify.com/album/6OfqOB3kZ1jlC3wGpcrQ9m"},
      ],
    }
  },
}
</script>