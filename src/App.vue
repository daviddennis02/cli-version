
<template>
  <div id="app">
    <h1>{{ restaurantName }}</h1>
    <p class="description">
      Welcome to {{ restaurantName }}! We are known for our freshly baked bread
      and french pastries! Give you morning a warm start or treat yourself in
      the middle of the day. Our butter is imported from local farmers in
      France. Once you take your first bite, you will see why everyone can't get
      enough!
    </p>
    <section class="menu">
      <h2>Menu</h2>
      <menuItem  addToShoppingCartFunc='addToShoppingCart' />
    </section>

    <aside class="shopping-cart">
      <h2>Shopping Cart: {{ shoppingCart }} items</h2>
    </aside>

    <h2>Contact Us</h2>
    <p>Address: {{ address }}</p>
    <p>Phone: {{ phone }}</p>
    <p>Email: {{ email }}</p>
    <p>Hours:</p>
    <ul>
      <li>M-F: 06:00 to 16:00</li>
      <li>Saturday: 07:00 to 14:00</li>
      <li>Sunday: 07:00 to 12:00</li>
    </ul>
    <footer class="footer">
      <p>{{ copyright }}</p>
    </footer>
  </div>
</template>

<script>
import MenuItem from "@/components/MenuItem";

export default {
  el: "#app",
  components: {
    MenuItem,
  },
  data: function () {
    return {
      address: "9274 Beurre Ave, Paris, France",
      email: "hello@cafewithavue.bakery",
      phone: "+08 88 88 88 88 88",
      restaurantName: "Cafe with A Vue",
      shoppingCart: 0,
    };
  },
  computed: {
    copyright() {
      const currentYear = new Date().getFullYear();
      return `Copyright ${this.restaurantName} ${currentYear}`;
    },
  },
  methods: {
    addToShoppingCart(amount) {
      this.shoppingCart += amount;
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

ul > li {
  list-style: none;
}

.description {
  max-width: 960px;
  font-size: 1.2rem;
  margin: 0 auto;
}

.footer {
  text-align: center;
  font-style: italic;
}

.menu {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.shopping-cart {
  position: absolute;
  right: 30px;
  top: 0;
}
</style>
