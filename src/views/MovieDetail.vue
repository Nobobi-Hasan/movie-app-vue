<script setup>

import { onMounted } from 'vue';
import {useMovieStore} from '../stores/movie'
import { useRoute } from 'vue-router';

const movieStore = useMovieStore();
const route = useRoute();

onMounted(() => {
    movieStore.getSingleMovie(route.params.id);
})

</script>

<template>

    <div class="movie-detail">

        <div class="title-rating">
            <h3 class="title">{{movieStore.singleMovie.Title}}</h3>

            <div class="imdb-rating">
                <h3 class="imdb"> <span>IMDB &nbsp;</span>Rating</h3>
                <h3 class="rating">{{movieStore.singleMovie.imdbRating}}/10</h3>
            </div>
            
        </div>
        
        <p>{{movieStore.singleMovie.Year}}</p>
       
        <div class="movie-image">

            <img :src="movieStore.singleMovie.Poster" alt="">

            <div class="movie-type">
                {{ movieStore.singleMovie.Type }}
            </div>

        </div>

        <div class="movie-genre">
            {{ movieStore.singleMovie.Genre }}
        </div>

        <p class="plot">{{ movieStore.singleMovie.Plot }}</p>
        <hr>

        <p>Director: &nbsp;{{ movieStore.singleMovie.Director }}</p>
        <hr>

        <p>Writer: &nbsp;{{ movieStore.singleMovie.Writer }}</p>
        <hr>

        <p>Actors: &nbsp;{{ movieStore.singleMovie.Actors }}</p>
        <hr>

        <p>Runtime: &nbsp;{{ movieStore.singleMovie.Runtime }}</p>
        <hr>

        <p>Released: &nbsp;{{ movieStore.singleMovie.Released }}</p>
        <hr>

        <p>Awards: &nbsp;{{ movieStore.singleMovie.Awards }}</p>
        <hr>

        <p>BoxOffice: &nbsp;{{ movieStore.singleMovie.BoxOffice }}</p>
        <hr>
        
        <p>Language: &nbsp;{{ movieStore.singleMovie.Language }}</p>
        <hr>

    </div>

</template>

<style lang="scss" scoped>

.movie-detail{
    padding: 16px;

    .title-rating{
        display: flex;
        justify-content: space-between;
        align-items: center;

        .title{
            color: white;
            font-size: 32px;
            font-weight: 600;
            margin-bottom: 16px;
        }

        .imdb-rating{
            color: white;

            span{
                color: yellow;
            }

            .imdb{
                font-size: 16px;
            }
            .rating{
                font-size: 28px;
            }
        
        }

    }

    // .movie-image{
    //     display: block;
    //     max-width: 200px;
    //     margin-bottom: 16px;
    // }

    .movie-image{
        position: relative;
        display: block;

        img{
            display: block;
            width: 100%;
            max-width: 200px;
            height: 300px;
            object-fit: cover;
        }

        .movie-type{
            position: absolute;
            padding: 8px 16px;
            background-color: #34d399;
            color: white;
            bottom: 16px;
            left: 0px;
            text-transform: capitalize;
        }

    }

    .movie-genre{
        display: inline-block;
        padding: 8px 16px;
        background-color: #34d399;
        color: white;
        margin-top: 16px;
        margin-bottom: 16px;
        left: 0px;
        text-transform: capitalize;
    }

    .plot{
        color: white;
    }

    p{
        color: rgb(167, 185, 212);
        font-size: 18px;
        line-height: 1.2;
        margin-top: 10px;
        margin-bottom: 10px;
        text-align: justify;
    }
}

</style>
