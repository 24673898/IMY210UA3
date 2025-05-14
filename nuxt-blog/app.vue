<!-- u24673898 Franky -->
<template>
  <div id="app">
    <!-- Header/Navigation -->
    <header class="header">
   <nav class="navbar">
  <div class="nav-container">
    <!-- Logo/Brand -->
    <NuxtLink to="/" class="logo">
      <h1>My Blog</h1>
    </NuxtLink>

    <!-- Navigation Menu -->
    <ul class="nav-menu push-right">
      <li class="nav-item">
        <NuxtLink to="/" class="nav-link" active-class="active">
          Home
        </NuxtLink>
      </li>
      <li class="nav-item">
        <NuxtLink to="/search" class="nav-link" active-class="active">
          Search
        </NuxtLink>
      </li>
    </ul>
  </div>
</nav>
    </header>

    <!-- Main Content Area -->
    <main class="main-content">
      <!-- This is where page content will be rendered -->
      <NuxtPage />
    </main>

    <!-- Footer -->
    <footer class="footer">
      <div class="footer-container">
        <p>&copy; 2025 My Blog. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
// You can add global head configuration here
useHead({
  title: 'My Blog',
  meta: [
    { name: 'description', content: 'A blog built with NuxtJS and Strapi' },
    { name: 'viewport', content: 'width=device-width, initial-scale=1' }
  ],
  htmlAttrs: {
    lang: 'en'
  }
})
</script>

<style scoped>
/* Global styles for the app layout */
#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

/* Header Styles */
.header {
  background-color: #333;
  color: white;
  padding: 1rem 0;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.nav-container {
 max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}

.push-right {
  margin-left: auto;
}

.logo {
  text-decoration: none;
  color: white;
}

.logo h1 {
  margin: 0;
  font-size: 1.5rem;
}

.nav-menu {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  gap: 2rem;
}

.nav-item {
  display: inline;
}

.nav-link {
  color: white;
  text-decoration: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  transition: background-color 0.3s;
}

.nav-link:hover,
.nav-link.active {
  background-color: #555;
}

/* Main Content */
.main-content {
  flex: 1;
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem 1rem;
  width: 100%;
}

/* Footer */
.footer {
  background-color: #f5f5f5;
  padding: 1rem 0;
  border-top: 1px solid #eee;
  margin-top: auto;
}

.footer-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
  text-align: center;
}

/* Responsive Design */
@media (max-width: 768px) {
  .nav-container {
    flex-direction: column;
    gap: 1rem;
  }
  
  .nav-menu {
    flex-direction: column;
    text-align: center;
    gap: 1rem;
  }
  
  .main-content {
    padding: 1rem;
  }
}
</style>