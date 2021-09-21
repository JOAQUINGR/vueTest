<template>

<div class="home">
  <h1>TOP FILMS BILLBOARD</h1>
  <p class="lead text-muted">Find the most interesting movies of the moment</p>
  <img src="https://m.media-amazon.com/images/M/MV5BYTc0NWIwOTYtNzEwYi00YmUyLTlmYWYtYjJiZjRjN2RjMjAxXkEyXkFqcGdeQXVyMTEyMjM2NDc2._V1_UX128_CR0,3,128,176_AL_.jpg">
    <div class="row">
      <div v-for="film in films" :key='film.id'>
        <div class="col-md-2 px-1 py-1">
        <router-link :to="{ name: 'Filmdetails', params: { id: film.id }}">
          <a data-toggle="modal" data-target='#' class="card h-100 btn p-1 btn-sm btn-outline-secondary" type="search" name="specie_name" value="film.id">
            <img class="bd-placeholder-img card-img-top" src='film.image'>
            <text x="50%" y="50%" fill="#eceeef" dy=".3em"><i>{{ film.year }}</i> <br>
              <strong>{{ film.title }}</strong>
            </text>
          </a>
          </router-link>
        </div>
      </div>
    </div>
</div>
</template>

<script>
export default {
  data () {
    return {
      films: []
    }
  },
  mounted () {
    fetch('https://imdb-api.com/en/API/MostPopularMovies/k_d26h1996')
      .then(res => res.json())
      .then(data => { this.films = data.items })
      .catch(err => console.log(err.message))
  }
}

</script>
