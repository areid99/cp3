<template>
<div>
  <h1 class = "wrapper">My Many Dogs!</h1>
  <p class = "wrapper">Have a look at my dogs! If you want to see a specific breed, search below! Leave some comments to let me know what you think!</p>
  <div class="wrapper">
    <div class="search">
      <form class="pure-form">
        <i class="fas fa-search"></i><input v-model="searchText" />
      </form>
    </div>
    <router-link :key="Math.floor(Math.random() * 20)" :to="'/product/' + Math.floor(Math.random() * 20)"><button>Visit Random Dog</button></router-link>

  </div>

  <ProductList :products="products" />
</div>
</template>

<script>
import ProductList from "../components/ProductList.vue"
export default {
  name: 'Home',
  components: {
    ProductList
  },
  data() {
    return {
      searchText: '',
    }
  },
  computed: {
  products() {
    return this.$root.$data.products.filter(product => product.breed.toLowerCase().search(this.searchText.toLowerCase()) >= 0);
  }
  },
}
</script>
<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.search {
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 50%;
}

form {
  display: table;
  width: 100%;
}

i {
  display: table-cell;
  padding-left: 10px;
  width: 1px;
}

input {
  display: table-cell;
  font-size: 20px;
  border: none !important;
  box-shadow: none !important;
  width: 100%;
  height: 40px;
}
</style>
