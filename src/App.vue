<template lang="pug">
  #app
    section.section
      nav.nav.has-shadow
        .container
          input.input.is-large(
            type="text", 
            placeholder="Buscar cancion",
            v-model="searchQuery" 
          )
          a.button.is-info.is-large(@click="search") Buscar
          a.button.is-danger.is-large &times

      .container
        p.has-text-centered 
          small {{searchMessage}}
        .columns

          .column(v-for="track in tracks") {{track.name}} - {{track.artist}}




</template>

<script>
const tracks = [
  {name:'Fade to black', artist:'Metallica'},
  {name:'The Way of Vikings', artist:'Amon Amarth'}, 
  {name:'Keeper of the seven keys', artist:'Helloween'}  
]
export default {
  name: 'app',

  data () {
    return {
      searchQuery: '',
      tracks:[]
    }
  },
  methods: {
    search () {
      this.tracks = tracks;
    }
  },
  computed:{
    searchMessage(){
      return `Encontrados: ${this.tracks.length}`
    }
  }
}
</script>

<style lang="scss">
  @import './scss/main.scss'
</style>
