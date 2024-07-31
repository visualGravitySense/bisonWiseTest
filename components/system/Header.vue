<template>
  <header>
    <div class="navbar">
      <div class="container">
        <div class="navbar-content">
          <div class="logo">
            <nuxt-link to="/">
              <img src="@/static/logo.png" alt="🦬BisonWise" width="50" height="45" /> <!-- Replace with the actual logo -->
            </nuxt-link>
          </div>
          <div class="form-group">
            <!-- <label for="phone">Search</label>
            <AppInput type="text" id="name"  required /> -->
            <AppSearch
              type="text"
              id="search"
              required
              label="Search"
              :icon="true"
            />
          </div>
          
          <div class="menu" :class="{ 'menu-open': isMenuOpen }">
            <ul class="navbar-list">
              <li class="navbar-item" v-for="link in links" :key="link.title">
                <nuxt-link class="navbar-link" :title="link.title" :to="link.url">{{ link.title }}</nuxt-link>
              </li>
            </ul>
            <div class="cta-buttons">
              <nuxt-link to="/signin" class="signin-button">Log in</nuxt-link>
              <nuxt-link to="/signup" class="signup-button">Join now</nuxt-link>
            </div>
          </div>
          <div class="burger-menu" @click="toggleMenu">
            <span class="burger-bar"></span>
            <span class="burger-bar"></span>
            <span class="burger-bar"></span>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      links: [
        { title: 'Категории', url: '/categories' },
        { title: 'О курсах', url: '/teachers' },
        { title: 'О нас', url: '/about' },
      ],
      isMenuOpen: false
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    }
  }
};
</script>

<style>

.form-group {
  flex: 1;
  max-width: 25%; /* Ensures inputs are not too small */
}

.form-group label {
  display: block;
  margin-bottom: 8px;
  font-weight: bold;
  color: #333;
}

.form-group input {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.navbar {
  background-color: #0f1624; /* Dark background */
  padding: 1rem 0;
}

.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo img {
  display: block;
}

.navbar-content {
  display: flex;
  align-items: center;
  width: 100%;
  justify-content: space-between;
}

.menu {
  display: flex;
  align-items: center;
}

.navbar-list {
  display: flex;
  list-style: none;
  padding: 0;
  margin: 0;
}

.navbar-item {
  margin-left: 1rem;
}

.navbar-link {
  color: #ffffff; /* White text */
  text-decoration: none;
  padding: 0.5rem 1rem;
  transition: color 0.3s;
}

.navbar-link:hover,
.navbar-link.nuxt-link-exact-active {
  color: #ffdc00; /* Yellow text on hover */
}

.cta-buttons {
  display: flex;
  align-items: center;
}

.signin-button {
  background-color: transparent;
  color: #ffdc00;
  border: 1px solid #ffdc00;
  padding: 0.5rem 1rem;
  text-decoration: none;
  border-radius: 0.25rem;
  transition: background-color 0.3s, color 0.3s;
}

.signup-button {
  background-color: #28a745; /* Green button */
  margin-left: 1rem;
  color: #ffffff;
  padding: 0.5rem 1rem;
  text-decoration: none;
  border-radius: 0.25rem;
  transition: background-color 0.3s, color 0.3s;
}

.signup-button:hover,
.signin-button:hover {
  background-color: #ffdc00; /* Yellow background on hover */
  color: #0f1624; /* Dark text on hover */
}

.burger-menu {
  display: none;
  flex-direction: column;
  cursor: pointer;
}

.burger-bar {
  width: 25px;
  height: 3px;
  background-color: #ffffff;
  margin: 4px 0;
  transition: 0.4s;
}

@media (max-width: 768px) {
  .menu {
    display: none;
    flex-direction: column;
    align-items: flex-start;
  }

  .menu.menu-open {
    display: flex;
    position: absolute;
    top: 60px;
    left: 0;
    background-color: #0f1624;
    width: 100%;
    padding: 1rem;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }

  .navbar-list {
    flex-direction: column;
    width: 100%;
  }

  .navbar-item {
    margin-left: 0;
    width: 100%;
  }

  .navbar-link {
    padding: 1rem;
    width: 100%;
    text-align: left;
  }

  .cta-buttons {
    flex-direction: column;
    width: 100%;
  }

  .signup-button,
  .signin-button {
    margin-left: 0;
    margin-top: 1rem;
    width: 100%;
    text-align: center;
  }

  .burger-menu {
    display: flex;
  }
}
</style>
