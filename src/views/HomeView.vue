<script setup>
import {useMovieStore} from '../stores/movie'
const movieStore = useMovieStore();

</script>

<template>
  <div class="home">
    <div class="featured-movie-card">

        <img src="https://images.unsplash.com/photo-1536440136628-849c177e76a1?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1025&q=80" alt="movie-image" class="featured-novie-image">

        <div class="movie-detail">
        </div>
    </div>

    <form @submit.prevent="movieStore.SarchMovies" class="search-box">
      <div class="search-box-div">
        <input type="text" placeholder="Search movie..." v-model="movieStore.search">
        <input type="submit" value="Search">
      </div>
    </form>

    <div class="movies-list">
      <div class="movie" v-for="movie in movieStore.movies" :key="movie.imdbID">
        <router-link :to="{name: 'movie-detail', params: {id: movie.imdbID}}" class="movie-link">
        
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
  .featured-movie-card{
    position: relative;

    .featured-novie-image{
      display: block;
      width: 100%;
      height: 35vh;
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

  .search-box-div{
    display: flex;
    flex-direction: row;
    justify-content:flex-start;
    align-items: center;
    padding: 2%;
    margin: 0px 8px;

    input{
      display: block;
      max-width: 50%;
      appearance: none;
      border: none;
      background: none;
      outline: none;
      margin-right: 10px;

      &[type = "text"]{

        @media (min-width:1200px) {          
          height: 50px;
          font-size: 20px;
        }

        @media (min-width:768px) and (max-width:1199px) {
          height: 45px;
          font-size: 18px;
        }

        @media (max-width:767px) {
          height: 40px;
          font-size: 16px;
        }

        width: 100%;
        color: white;
        background-color: #496583;
        padding: 10px 16px;
        border-radius: 8px;
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
        max-width: 250px;

        @media (min-width:1200px) {          
          height: 50px;
          font-size: 20px;
        }

        @media (min-width:768px) and (max-width:1199px) {
          height: 45px;
          font-size: 18px;
        }

        @media (max-width:767px) {
          height: 40px;
          font-size: 16px;
        }
        
        background-color: #34d399;
        border-radius: 8px;
        color: white;
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

      @media (min-width:1650px) {

        max-width: 20%;
        flex: 1 1 20%;
        padding: 16px 2%;

      }

      @media (min-width:1200px) and (max-width:1649px) {

        max-width: 25%;
        flex: 1 1 25%;
        padding: 16px 2%;

      }

      @media (min-width:768px) and (max-width:1199px) {

        max-width: 33%;
        flex: 1 1 33%;
        padding: 16px 2%;

      }

      @media (max-width:767px) {

        max-width: 50%;
        flex: 1 1 50%;
        padding: 16px 2%;

      }

      
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
