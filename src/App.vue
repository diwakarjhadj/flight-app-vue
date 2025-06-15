<template>
  <div id="app">
    <header class="app-header">
      <a href="https://www.gowithgbi.com/" target="_blank" class="logo-link">
        <img :src="logo" alt="GB International Logo" class="logo" />
      </a>
      <div class="header-text">
        <h1>GB International</h1>
        <p>Select your source and destination to view available flights.</p>
      </div>
    </header>

    <main>
      <FlightApp />
    </main>

    <footer>
      <p>&copy; 2025 GB International. All rights reserved.</p>
    </footer>
  </div>
</template>

<script>
import logo from './assets/logo.jpg';
import FlightApp from './components/FlightApp.vue';

export default {
  name: 'App',
  components: {
    FlightApp,
  },
  data() {
    return {
      logo,
    };
  },
};
</script>

<style>
/* Apply full-screen layout */
#app {
  font-family: Arial, sans-serif;
  color: #333;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.app-header {
  display: flex;
  align-items: center;
  gap: 15px;
  padding: 20px;
  border-bottom: 2px solid #ddd;
  margin-bottom: 20px;
  background-color: #0e1464;
  color: #fff;
}

.logo {
  width: 50px;
  height: 50px;
  object-fit: contain;
  margin-right: 10px;
  border-radius: 50%;
  cursor: pointer;
}

.header-text {
  text-align: center;
  width: 90%;
}

h1 {
  font-size: 1.8rem;
  margin: 0;
}

p {
  font-size: 1rem;
  margin: 5px 0 0;
}

main {
  flex: 1; /* Takes up remaining space */
  padding: 20px;
}

footer {
  background-color: #333;
  color: white;
  padding: 10px 0;
  font-size: 0.9rem;
  text-align: center;
}
body{
  margin: 0px;
}
</style>
