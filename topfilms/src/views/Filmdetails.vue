<template>

    <h3>FILM DETAILS</h3>
    <h5> the id is {{ id }}</h5>

</template>

<script>
export default {
  props: ['id'],
  data () {
    return {
      film: null
    }
  },
  mounted () {
    fetch('https://imdb-api.com/en/API/Title/k_d26h1996/' + this.id)
      .then(res => res.json())
      .then(data => { this.film = data })
      .catch(err => console.log(err.message))
  }
}

</script>
