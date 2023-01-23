<template>
  <div class="container grey darken-3">
    <h4 class="white-text black" style="text-align: center;">TOP RUBICK CUBES</h4>
    <div class="row container">
      <div v-for="product in Allproducts" class="col s12 m4 grey darken-3">
        <div class="card col m12 s12 grey darken-4">
          <div class="card-image">
            <img :src= "product.image"/>
            <button
              class="btn-floating halfway-fab waves-effect waves-light red"
            >
              <i class="material-icons">add</i>
            </button>
          </div>
          <div class="card-title black white-text">
            {{ product.name }}
          </div>
          <div class="card-content grey darken-3 white-text">
            Price: {{ product.price }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "products",
  data() {
    return {
      Allproducts: [
        {
          name: "GAN 12 M",
          price: 360000,
          total: 0,
          image: "/assets/gan12.webp",
        },
        {
          name: "Shashibo",
          price: 266918,
          total: 0,
          image: "/assets/shapes.webp"
        },
        {
          name: "wowcube",
          price: 1838000,
          total: 0,
          image: "/assets/wowcube-preview.jpg"
        },
      ],
    };
  },
};
</script>
