<template>
  <div>
    <section>
      <h1
        class="mb-4 text-4xl font-extrabold leading-none tracking-tight text-gray-900 md:text-5xl lg:text-6xl dark:text-white">
        Fetured Movies</h1>

      <ul class="grid grid-cols-3 gap-3 items-stretch">
        <li v-for="movie in movies" :key="movie.id">
          <MovieCard :poster_path="movie.poster_path" :title="movie.title" :id="movie.id" :overview="movie.overview"
            :release_date="movie.release_date" :popularity="movie.popularity" :item="movie" />
        </li>
      </ul>
    </section>
    <section>
      <h1
        class="mb-4 text-4xl font-extrabold leading-none tracking-tight text-gray-900 md:text-5xl lg:text-6xl dark:text-white">
        Fetured TV Series</h1>

      <ul class="grid grid-cols-3 gap-3">
        <li v-for="serie in series" :key="serie.id">
          <MovieCard :poster_path="serie.poster_path" :name="serie.name" :id="serie.id" :overview="serie.overview"
            :first_air_date="serie.first_air_date" :popularity="serie.popularity" :item="serie" />
        </li>
      </ul>
    </section>
  </div>
</template>

<script setup>
const movies = useState(() => [])
const series = useState(() => [])

const { data } = await useFetch('api/movies/discover', {
  transform: (data) => {
    movies.value = data.movies.results
    series.value = data.series.results
  }
})
</script>