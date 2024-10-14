<template>
  <form @submit.prevent="submitForm" class="product-form">
    <div>
      <label for="name">Product Name:</label>
      <input type="text" v-model="name" />
    </div>
    <div>
      <label for="price">Price:</label>
      <input type="number" v-model="price" />
    </div>
    <div>
      <label for="description">Description:</label>
      <textarea v-model="description"></textarea>
    </div>
    <button type="submit">Add Product</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      price: 0,
      description: ''
    };
  },
  methods: {
    submitForm() {
      const product = {
        name: this.name,
        price: this.price,
        description: this.description
      };
      this.$emit('add-product', product);
      this.name = '';
      this.price = 0;
      this.description = '';
    }
  }
};
</script>

<style scoped>
.product-form {
  background-color: #ba68c8;
  padding: 20px;
  border-radius: 10px;
  width: 300px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  color: white;
}

.product-form input,
.product-form textarea {
  width: 100%;
  margin: 10px 0;
  padding: 8px;
  border-radius: 5px;
  border: 1px solid #7b1fa2;
}

button {
  background-color: #7b1fa2;
  border: none;
  padding: 10px;
  width: 100%;
  color: white;
  font-weight: bold;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #4a0072;
}
</style>
