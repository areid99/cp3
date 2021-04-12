<template>
<div class="wrapper">
  <div class="products">
    <div class="product" v-for="product in products" :key="product.id">
      <div class="info">
        <h2>{{product.name}}: {{product.age}}</h2>
        <p>{{product.breed}}</p>
      </div>

      <div class="image">
        <img :src="'/images/Dog_Pics/'+product.image">
      </div>
      <router-link :key="product.id" :to="'/product/' + product.id"><button>Visit!</button></router-link>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'ProductList',
  props: {
    products: Array
  },

data() {
  return {
  }
},
  methods: {
    },
  }
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.products {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.product {
  margin: 10px;
  margin-top: 50px;
  width: 60%;
}

.product img {
  border: 2px solid #333;
  height: 500px;
  width: 60%;
  object-fit: cover;
}

.product .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #37FEE7;
  color: #000;
  padding: 10px 30px;
  height: 80px;
}



.info h2 {
  font-size: 20px;
  margin: 10px;
  display: flex;
  justify-content: center;
}

.info p {
  margin: 0px;
  font-size: 14px;
  display: flex;
  justify-content: center;
}


button {
  height: 50px;
  background: #37DEFE;
  color: black;
  border: none;
  width: 100%
}

.auto {
  margin-left: auto;
}
</style>
