<template>
  <div v-if="prod" class="product" :style="`background-color: ${bgType(prod)}`">
    <ProductCard :prod="prod" />
    <button
      class="product__button product__button--comprar"
      @click="setItemCart(prod)"
    >
      Comprar
    </button>
    <a href="#contact" class="product__button product__button--falar"
      >Fale Conosco</a
    >
  </div>
</template>

<script>
import { mapActions } from 'vuex'
export default {
  name: 'ProductslayoutComponent',
  props: {
    prod: {
      type: Object,
      required: true,
    },
  },
  methods: {
    ...mapActions({
      setItemCart: 'cart/setItemCart',
    }),
    bgType(prod) {
      return [
        ...new Set(
          prod.types.map(x => {
            return x.type.name === 'grass'
              ? '#81BD8C'
              : x.type.name === 'poison'
              ? '#81BD8C'
              : x.type.name === 'fire'
              ? '#FFA860'
              : x.type.name === 'flying'
              ? '#B0BFD8'
              : x.type.name === 'water'
              ? '#37A7F2'
              : '#B0BFD8'
          }),
        ),
      ][0]
    },
  },
}
</script>

<style lang="scss" scoped>
.product {
  width: 250px;

  display: flex;
  flex-direction: column;
  align-items: center;
  border-radius: 15px;
  padding: 40px 0 50px 0;
  &__button {
    width: 80%;
    height: 50px;
    border: none;
    border-radius: 10px;
    margin-top: 20px;
    font-size: 16px;
    font-weight: bold;
    color: white;
    cursor: pointer;
    transition: all 0.1s ease-in-out;
    &:hover {
      transition: all 0.1s ease-in-out;
      transform: scale(1.02);
    }
  }
  &__button--comprar {
    background-color: #f78600;
    box-shadow: 3px 3px #c26c03;
  }
  &__button--falar {
    background-color: #1686f0;
    box-shadow: 3px 3px #004d95;
    display: flex;
    align-items: center;
    justify-content: center;
    text-decoration: none;
  }
}
@media (min-width: 1024px) {
  .product {
    width: 300px;
    padding: 60px 0 50px 0;
  }
}
</style>
