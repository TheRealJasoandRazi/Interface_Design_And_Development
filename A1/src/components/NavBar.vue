<template>
    <nav class="col-12 navbar">
        <div class="navbar-content">
          <div class="navbar-title">Event Management System</div>
          <ul class="navbar-menu">
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#contact">Contact</a></li>
          </ul>
        </div>
    </nav>
</template>

<style scoped>
    .navbar {
  background-color: #333;
  padding: 1rem;
}

.navbar-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
}

.navbar-title {
  color: white;
  font-size: 1.5rem;
  font-weight: bold;
}

.navbar-menu {
  list-style: none;
  display: flex;
  padding: 0;
  margin: 0;
}

.navbar-menu li {
  margin: 0 15px;
}

.navbar-menu a {
  color: white;
  text-decoration: none;
  font-size: 1.2rem;
}

.navbar-menu a:hover {
  text-decoration: underline;
}
</style>