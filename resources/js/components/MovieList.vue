<template>
    <div class="container">
        <h1>Movie List</h1>
        <div class="row">
            <div v-for="(movie, index) in movies" :key="index" class="col-md-4">
                <div class="card movie-card">
                    <div class="card-body">
                        <img :src="'storage/imgs/' + movie.image_filename + '.jpg'" :title="movie.title" :alt="movie.title">
                    </div>
                </div>
            </div>
            <div class="col-md-4">
                <div class="card movie-card">
                    <div class="card-body">
                        <p>MOVIE</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data: function () {
            return {
                movies: []
            }
        }, mounted() {
            axios.get("/api/movies").then((response) => {
                this.movies = response.data;
            }).catch((error) => {
                console.log(error);
            });
        }
    }
</script>

<style scoped>
    img {
        height: 368px;
        width: 238px;
    }

    .movie-card {
        height: 400px;
        width: 270px;
        margin-top: 1em;
        border: 0px;
    }
</style>
