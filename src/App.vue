<script setup>

</script>

<template>

  <header>
    <routerLink :to="{name: 'home'}">
      <h1>Movies <span>App</span></h1>
    </routerLink>
  </header>

  <main>

    <div class="container">
      
      <router-view></router-view>

    </div>

  </main>

</template>

<style lang="scss">

@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;500;700;900&display=swap');

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Montserrat', sans-serif;

  &::selection{
    background: transparentize($color: #34d399, $amount: 0.5);
  }
}

body{
  background-color: #4b5563;
}

a{
  text-decoration: none;
}

header{
  display: flex;
  text-align: center;
  justify-content: center;
  padding: 10px 16px;
  background-color: #1e293b;
  box-shadow: 0px 0px 6px rgba($color: #000000, $alpha: 0.1);
}

h1{
  color: white;
  font-size: 28px;
  span{
    color: #34d399;
  }
}

.container{
  max-width: 900px;
  margin-left: auto;
  margin-right: auto;
}

</style>
