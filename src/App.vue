<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Lobby</router-link>|
      <router-link to="/Game">Game</router-link>|
      <router-link to="/about">About</router-link>|
      <router-link to="/chat">Chat</router-link>
    </div>
    <router-view />
  </div>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Merriweather:wght@400;700;900&display=swap");
html,
body {
  margin: 0;
}

body {
  background-color: #fafafa;
}

#app {
  font-family: "Merriweather";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
