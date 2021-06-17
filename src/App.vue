<template>
  <div class="container" id="app">
    <div class="header">
      <div id="nav">
        <img
          alt="Brainstud logo"
          src="./assets/Logo_Brainstud_horizontaal.png"
        />
        <router-link to="/">Home</router-link> |
        <router-link to="/about">About</router-link>
      </div>
    </div>
    <div class="main">
      <router-view />
    </div>
    <div class="footer">
      <img alt="Brainstud logo" src="./assets/Tagline_LAM.png" />
    </div>
  </div>
</template>

<style lang="scss">
@font-face {
  font-family: Gilroy;
  src: url("./assets/Gilroy-ExtraBold.otf") format("opentype");
}

@font-face {
  font-family: Eina;
  src: url("./assets/Eina03-Regular.ttf") format("truetype");
}

@font-face {
  font-family: EinaBold;
  src: url("./assets/Eina03-Bold.ttf") format("truetype");
}

$primary-color: #6400cd;
$secondary-color: #7800a0;
$accent-color: #ff6e32;

html {
  height: 100%;
}

body {
  background: #f0f2ff;
  height: 100%;
  display: block;
  padding: 0;
  margin: 0;

  font-family: Eina;
  font-size: 14px;
  line-height: 19.26px;
}

h1 {
  font-family: Gilroy;
  font-size: 25px;
  line-height: 30.63px;
}

h2 {
  font-family: Gilroy;
  font-size: 20px;
  line-height: 24.5px;
}

h3 {
  font-family: Gilroy;
  font-size: 18px;
  line-height: 22.05px;
}

p {
  font-family: Eina;
  font-size: 14px;
  line-height: 19.26px;
  padding-bottom: 21px;
}

.button {
  color: #fff;
  text-decoration: none;
  padding: 7px 26px;
  border-radius: 30px;
  border: 0;
  cursor: pointer;

  &.button-primary {
    background-color: $primary-color;
  }

  &.button-secondary {
    background-color: $secondary-color;
  }

  &:disabled {
    background-color: #bebed2;
    cursor: not-allowed;
  }
}

input[type="text"] {
  background: #ffffff;
  border: 1px solid #1e1e32;
  box-sizing: border-box;
  border-radius: 30px;
  width: 100%;
  line-height: 35px;
  padding: 0 16px;

  &:focus {
    outline: none;
  }
}

.container {
  display: grid;
  height: 100%;
  align-content: stretch;
  grid-template-columns: 1fr minmax(auto, 959px) 1fr;
  grid-template-rows: 1fr minmax(554px, auto) 1fr;
  grid-template-areas:
    ". header ."
    ". main ."
    ". footer .";
}

.header {
  grid-area: header;
  text-align: left;
}

.main {
  grid-area: main;
  border-radius: 30px;
  background: #fff;
  box-shadow: 0 0 25px rgba($color: #000000, $alpha: 0.25);
  padding: 42px;
}

.footer {
  grid-area: footer;
  text-align: left;
  align-self: center;
}
</style>
