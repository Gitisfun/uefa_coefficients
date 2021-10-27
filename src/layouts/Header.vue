<template>
  <header>
    <img width="45px" src="../assets/football-logo.png" alt="logo" />
    <nav>
      <ul class="nav_links">
        <li><a href="#">Home</a></li>
        <li><a href="#">Country ranking</a></li>
        <li><a href="#">Club ranking</a></li>
        <li><a href="#">Calculation</a></li>
        <li><a href="#">About</a></li>
      </ul>
    </nav>
    <a href="#"><button>Contact</button></a>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@500&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

li,
a,
button {
  font-family: "Montserrat", sans-serif;
  font-weight: 500;
  font-size: 16px;
  color: #edf0f1;
  text-decoration: none;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 30px 10%;
  height: 70px;
  background-color: #24252a;
  }

.logo {
  cursor: pointer;
}

.nav_links {
  list-style: none;
}

.nav_links li {
  display: inline-block;
  padding: 0px 20px;
}

.nav_links li a {
  transition: all 0.3s ease 0s;
}

.nav_links li a:hover {
  color: #0088a9;
}

button {
  padding: 9px 25px;
  background-color: #3CE2FB;
  border: none;
  border-radius: 50px;
  cursor: pointer;
  transition: all 0.3s ease 0s;
}

button:hover {
  background-color: #3CE2FB;
}
</style>
