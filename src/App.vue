<template>
  <div id="app">
    <link
      href="https://fonts.googleapis.com/css?family=Satisfy"
      rel="stylesheet"
    />
    <h1 class="title">Czy umiesz tabliczkę mnożenia?</h1>
    <img id="play" class="image" src="./assets/PLAY.png" />
    <img id="read" class="image" src="./assets/READ.png" />
    <img id="test" class="image" src="./assets/TEST.png" />
    <img id="fb" class="image" src="./assets/FACEBOOK.png" />
    <!--<div id="nav"><router-link to="/">Strona główna</router-link> |</div>-->
    <div class="container"><router-view /></div>
    <p><small><strong>Jak grać? Podaj odpowiedź i wciśnij "Enter" lub kliknij przycisk sprawdź</strong></small>
    <br/><br/><a href="/game/about"
        ><svg
          fill="#fff"
          height="30"
          viewBox="0 0 24 24"
          width="30"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path id="path4138" d="m0 0h24v24h-24z" fill="none"></path>
          <path
            id="path4140"
            d="m15 2.5c-6.9 0-12.5 5.6-12.5 12.5s5.6 12.5 12.5 12.5 12.5-5.6 12.5-12.5-5.6-12.5-12.5-12.5zm-0.004 5.3281c0.501 0 0.926 0.1758 1.277 0.5274 0.352 0.345 0.528 0.7682 0.528 1.2695 0 0.508-0.176 0.937-0.528 1.289-0.345 0.345-0.769 0.516-1.277 0.516-0.501 0-0.93-0.176-1.281-0.528-0.345-0.351-0.516-0.776-0.516-1.277 0-0.5013 0.171-0.9245 0.516-1.2695 0.351-0.3516 0.78-0.5274 1.281-0.5274zm-1.601 5.2809h3.203v9.063h-3.203v-9.063z"
            transform="scale(.8)"
          ></path></svg
      ></a></p>
  </div>
</template>

<style lang="scss">
.container{
  animation: fadein .2s;
}

@keyframes fadein {
    from { opacity: 0;transform:translateY(300px) }
    to   { opacity: 1; transform:translateY(0)}
}
a{color:#fff}
body,
html {
  overflow: hidden;
  padding: 0;
  margin: 0;
}
body {
  padding: 30px;
}
.title {
  font: 900 7vmin satisfy, cursive;
  color: #f9f9f9;
  text-shadow: -4px -1px 0px #020202;
  max-width: 40%;
  margin: 3vmin auto;
}
.image {
  position: absolute;
  z-index: 0;
}
#fb {
  top: -47px;
  right: -39px;
  max-width: 316px;
}

#play {
  top: -52px;
  left: -4px;
  max-width: 316px;
}
#test {
  left: -48px;
  bottom: -15px;
  max-width: 300px;
}
#read {
  bottom: -30px;
  right: 0;
  max-width: 316px;
}
#app {
  background-color: #7cd4df;
  background-image: linear-gradient(#d4d5db4d 1px, transparent 1px), linear-gradient(90deg, #dcdcdc4d 1px, transparent 1px), linear-gradient(#dcdcdc4d 1px, transparent 1px), linear-gradient(90deg, rgba(255, 255, 255, 0.1) 1px, transparent 1px);
background-size: 20px 20px, 20px 20px, 20px 20px, 20px 20px;
    background-position: -2px -2px, -2px -2px, -1px -1px, -1px -1px;
  border-radius: 148px 35px 159px 23px;
  -moz-border-radius: 148px 35px 159px 23px;
  -webkit-border-radius: 148px 35px 159px 23px;
  border: 0px groove #7cd4df;
  position: relative;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;

 width: calc(80vw - 40px);
    height: calc(100vh - 120px);

  padding: 30px;
  margin: auto;
}

#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
