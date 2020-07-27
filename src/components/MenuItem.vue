<template>
  <div>
    <div v-for="item in simpleMenu" :key="item.name" class="menu-item">
      <img
        class="menu-item__image"
        :src="item.image.source"
        :alt="item.image.alt"
      />
      <div>
        <h3>{{ item.name }}</h3>
        <p v-if="item.inStock">In Stock</p>
        <p v-else>Out of Stock</p>
        <div>
          <label for="add-item-quantity">Quantity: {{ item.quantity }}</label>
          <input
            v-model.number="item.quantity"
            id="add-item-quantity"
            type="number"
          />
          <button @click="addToShoppingCart(item.quantity)">
            Add to Shopping Cart
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['addToShoppingCartFunc'],
  data: function() {
    return {
      simpleMenu: [
        {
          name: "Crossiant",
          image: {
            source: "images/crossiant.jpg",
            alt: "A crossiant",
          },
          inStock: true,
          quantity: 1,
        },
        {
          name: "French Baguette",
          image: {
            source: "images/french-baguette.jpeg",
            alt: "Four French Baguettes",
          },
          inStock: true,
          quantity: 1,
        },
        {
          name: "Éclair",
          image: {
            source: "images/eclair.jpg",
            alt: "Chocolate Éclair",
          },
          inStock: false,
          quantity: 1,
        },
      ],
    };
  },
  methods: {
    addToShoppingCart(amount) {
      this.addToShoppingCartFunc(amount);
    }
  },
};
</script>

<style scoped>
.menu-item {
  display: flex;
  width: 500px;
  justify-content: space-between;
  margin-bottom: 30px;
}

.menu-item__image {
  max-width: 300px;
}
</style>
