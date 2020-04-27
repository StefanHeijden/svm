<template>
  <v-carousel
      interval="4800"
      height="100%"
      hide-delimiter-background
      show-arrows-on-hover
    >
    <!--First card-->
      <v-carousel-item>
        <infosheet/>
      </v-carousel-item>
    <!--Second card-->
      <v-carousel-item>
        <spsheet/>
      </v-carousel-item>
    <!--Third card-->
      <v-carousel-item>
        <toursheet/>
      </v-carousel-item>
    </v-carousel>
</template>

<script>
import infosheet from './Info-Sheets/Info-Sheet'
import spsheet from './Info-Sheets/SP-Sheet'
import toursheet from './Info-Sheets/Tour-Sheet'

export default {
  name: 'info',
  components: {
    infosheet,
    spsheet,
    toursheet
  },
  data () {
    return {
    }
  },
}
</script>