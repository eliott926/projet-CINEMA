<template>
  <header>
  <div class="accueil">

    <h1>Recherche de films PWA</h1>
    <h2>Rechercher et critiquer des films</h2>

  </div>

  </header>

</template>


<style lang ="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Fira Sans', sans-serif;

  &::selection {
    background: transparentize(#42B883, 0.5);
  }
}
body {
  background-color: #35495E;
  background-position: center;
}

a {
  text-decoration: none;
}

header {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 16px;
  background-color: #2C3D4E;
  box-shadow: 0px 0px 6px rgba(0, 0, 0, 0.1);

  h1 {
    color: #FFF;
    font-size: 28px;
  }

  h2 {
    color: #FFF;
    font-size: 19px;
  }

  span {
    color: #42B883;
  }
  .sub {
    position: absolute;
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
  }

}




</style>