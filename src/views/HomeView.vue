<script setup>
import {useMovieStore} from '../stores/movie'

const movieStore = useMovieStore();




</script>

<template>
  <div class="home">
    <div class="featured-novie-card">
      <router-link to="/movie/tt0078346">

        <img src="https://images.unsplash.com/photo-1536440136628-849c177e76a1?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1025&q=80" alt="movie-image" class="featured-novie-image">

        <div class="movie-detail">
          <h3>Superman</h3>
          <p>An alien orphan is sent from his dying planet to Earth, where he grows up to become his adoptive home's first and greatest superhero.</p>
        </div>
      
      </router-link>
    </div>

    <form @submit.prevent="movieStore.SarchMovies" class="search-box">
      <div class="">
        <input type="text" placeholder="Search movie..." v-model="movieStore.search">
        <input type="submit" value="Search">
      </div>
    </form>

    <div class="movies-list">
      <div class="movie" v-for="movie in movieStore.movies" :key="movie.imdbID">
        <router-link to="/movie/" class="movie-link">
        
          <div class="movie-image">

            <img :src="movie.Poster" alt="">

            <div class="movie-type">
              {{ movie.Type }}
            </div>

          </div>

          <div class="movie-detail">
            <p class="movie-year">{{movie.Year}}</p>
            <h3>{{movie.Title}}</h3>
          </div>

        </router-link>
      </div>
    </div>

  </div>
</template>


<style lang="scss">

.home{
  .featured-novie-card{
    position: relative;

    .featured-novie-image{
      display: block;
      width: 100%;
      height: 300px;
      object-fit: cover;
      position: relative;
      z-index: 0;
    }

    .movie-detail{
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: rgba(0, 0, 0, 0.6);
      padding: 16px;
      z-index: 1;

      h3{
        color: white;
        margin-bottom: 16px;
      }

      p{
        color: white;
      }
    }

  }

  .search-box{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 16px;

    input{
      display: block;
      appearance: none;
      border: none;
      background: none;
      outline: none;

      &[type = "text"]{
        width: 100%;
        color: white;
        background-color: #496583;
        font-size: 20px;
        padding: 10px 16px;
        border-radius: 8px;
        margin-bottom: 15px;
        transition: 0.4s;
        
        &::placeholder{
          color: #f3f3f3;
        }

        &:focus{
          box-shadow: 0px 0px 6px rgba($color: #000000, $alpha: 0.4);
        }
      }

      &[type = "submit"]{
        width: 100%;
        max-width: 300px;
        background-color: #34d399;
        padding: 16px;
        border-radius: 8px;
        color: white;
        font-size: 20px;
        text-transform: uppercase;
        transition: 0.4s;

        &:active{
          background-color: #064e3b;
        }
      }
    }
  }

  .movies-list{
    display: flex;
    flex-wrap: wrap;
    margin: 0px 8px;

    .movie{
      max-width: 50%;
      flex: 1 1 50%;
      padding: 16px 8px;

      .movie-link{
        display: flex;
        flex-direction: column;
        height: 100%;

        .movie-image{
          position: relative;
          display: block;

          img{
            display: block;
            width: 100%;
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

        .movie-detail{
          background-color: #496583;
          padding: 16px 8px;
          flex: 1 1 100%;
          border-radius: 0px 0px 8px 8px;

          .movie-year{
            color: #aaa;
            font-size: 14px;
          }

          h3{
            color: white;
            font-weight: 600;
            font-size: 18px;
          }
        }

      }

    }

  }

}



</style>
