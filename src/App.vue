<template>
  <div id="app" class="container-fluid flex-centred column">
    <div class="nav container">
      <router-link class="nav-button" exact-active-class="active" to="/">Обновить</router-link>
      <router-link class="nav-button" active-class="active" to="/logout">Выход</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style scooped>
.nav {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  padding: 10px 0px;
}

.nav-button {
  border: none;
  outline: transparent;
  background-color: #000;
  color: #fff;
  padding: 10px 20px;
  border-radius: 5px;
  text-decoration: none;
}
.nav-button:first-child {
  margin-right: 10px;
}

.nav-button.active {
  background-color: darkgray;
}
</style>

<style>
#app {
  font-family: sans-serif;
}
.container {
  width: 1200px;
  max-width: 1200px;
  box-sizing: border-box;
  margin-bottom: 30px;
}

.container-fluid {
  width: 100%;
}

.flex-centred {
  display: flex;
  align-items: center;
  justify-content: center;
}

.column {
  flex-direction: column;
}
</style>