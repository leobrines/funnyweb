<template>

  <section class="section">
    <section class="hero">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">
            Top Funny Pug/competitivo
          </h1>
          <h2 class="subtitle">
            Premio a los mejores 3 jugadores
          </h2>
        </div>
        <br>
        <div class="columns is-mobile">
          <b-table :data="players" :columns="columns"></b-table>
        </div>
      </div>
    </section>
  </section>
</template>

<script>
export default {
  name: 'HomePage',
  data () {
    return {
      players: [],
      columns: [
        {
          field: 'name',
          label: 'Nombre'
        },
        {
          field: 'kills',
          label: 'Frags'
        },
        {
          field: 'deaths',
          label: 'Muertes'
        }
      ]
    }
  },
  created () {
    this.getTop()
  },
  methods: {
    async getTop () {
      const data = await this.$axios.$get('http://localhost:8080/top')

      if (data !== undefined) {
        this.players = data.players
        console.log(this.players)
      }
    }
  }
}
</script>
