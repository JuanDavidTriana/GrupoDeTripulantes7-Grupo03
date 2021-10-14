<template>
  <BasicLayouts>
    <br>
    <h1>Tienda de mascotas</h1>
    <br>
    <br>
    <br>
    <div class="ui grid">
      <div
        class="sixten wide mobile eight wide tablet four wide computer column"
        v-for="product in products"
        :key="product.id"
      >
        <Product :product="product" />
      </div>
    </div>
        <!-- Inicio de Sección la ubicacion y contacto de la pagia web  -->
    <div></div>
  <!-- Final de la sección de ubicación y contacto  -->
  </BasicLayouts>
</template>

<script>
import { ref, onMounted } from 'vue';
import BasicLayouts from '../layouts/BasicLayouts.vue';
import { getProducts } from '../api/products';
import Product from '../components/Product.vue';
export default {
  name: 'Home',
  components: {
    BasicLayouts,
    Product,
  },

  setup() {
    let products = ref(null);

    onMounted(async () => {
      const response = await getProducts(20);
      products.value = response;
    });
    return {
      products,
    };
  },
};
</script>
