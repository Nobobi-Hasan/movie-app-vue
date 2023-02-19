<script setup>

</script>

<template>

  <header>
    <routerLink :to="{name: 'home'}">
      <h1>Movie <span>Sc<span class="oo">00</span>pe</span></h1>
    </routerLink>
  </header>

  <main>

    <div class="container">
      
      <router-view></router-view>

    </div>

  </main>

  <footer>
    <div class="footer">
      <p>Developed by: <span>Md. Nabobi Hasan</span></p>
    </div>
  </footer>

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
  position: relative;
  min-height: 100vh;
  background-color: #4b5563;
  display: flex;
  flex-direction: column;
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
    font-size: 28px;
    color: #34d399;
    span{
      font-size: 34px;
      color: yellow;
    }
  }
}

.container{
  max-width: 100%;
  margin-left: auto;
  margin-right: auto;
  padding-bottom: 50px;
}

.footer{
  margin-top: auto;
  position:absolute;
  bottom:0px;
  width: 100%;
  height: 50px;
  background-color: rgba(0, 0, 0, 0.3);
  padding: 16px;
  z-index: 1;

  p{
    text-align: center;
    color: white;
    span{
      color: #34d399;
    }
  }
}

</style>
