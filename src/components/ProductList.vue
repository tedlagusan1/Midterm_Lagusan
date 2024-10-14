<template>
  <div>
    <ul class="product-list">
      <li v-for="(product, index) in products" :key="index">
        <div v-if="editingIndex === index" class="edit-form">
          <input v-model="editedProduct.name" placeholder="Edit name" />
          <input v-model="editedProduct.price" placeholder="Edit price" />
          <textarea v-model="editedProduct.description"></textarea>
          <button @click="saveEdit(index)">Save</button>
        </div>
        <div v-else>
          <strong>{{ product.name }}</strong> - ${{ product.price }}
          <p>{{ product.description }}</p>
          <button @click="editProduct(index)">Edit</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['products'],
  data() {
    return {
      editingIndex: null,
      editedProduct: {}
    };
  },
  methods: {
    editProduct(index) {
      this.editingIndex = index;
      this.editedProduct = { ...this.products[index] };
    },
    saveEdit(index) {
      this.$emit('edit-product', { index, product: this.editedProduct });
      this.editingIndex = null;
    }
  }
};
</script>

<style scoped>
.product-list {
  list-style-type: none;
  padding: 0;
  width: 300px;
  margin-top: 20px;
}

.product-list li {
  background-color: #ab47bc;
  color: white;
  margin-bottom: 10px;
  padding: 15px;
  border-radius: 5px;
}

.product-list button {
  background-color: #6a1b9a;
  border: none;
  padding: 5px 10px;
  color: white;
  font-weight: bold;
  border-radius: 5px;
  cursor: pointer;
}

.product-list button:hover {
  background-color: #4a0072;
}

.edit-form input,
.edit-form textarea {
  width: 100%;
  margin: 5px 0;
  padding: 8px;
  border-radius: 5px;
  border: 1px solid #7b1fa2;
}
</style>
