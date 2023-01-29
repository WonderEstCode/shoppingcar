<template>
  <div>
    <div class="nav-wrapper black">
      <a href="#" class="brand-logo">
        <i class="medium material-icons white-text">grid_on</i>
      </a>
      <ul class="right">
        <li>
          <button
            v-if="totalPrice > 0"
            @click="
              showCar = true;
              buyAgain = false;
            "
            class="waves-effect waves-light btn red"
            style="margin-right: 10px"
          >
            <i class="medium material-icons">shopping_cart</i>
            {{ sumProducts }}
          </button>
        </li>
      </ul>
      <ul class="left">
        <li>
          <a class="waves-effect waves-light btn black">CUBERS</a>
        </li>
      </ul>
    </div>
    <div v-show="buyAgain" class="container grey darken-3">
      <h4 class="white-text black" style="text-align: center">
        TOP RUBICK CUBES
      </h4>
      <div class="row container">
        <div v-for="product in Allproducts" class="col s12 m4 grey darken-3">
          <div class="card col m12 s12 grey darken-4">
            <div class="card-image">
              <img :src="product.image" />
            </div>
            <div class="card-title black white-text">
              {{ product.name }}
            </div>
            <div class="card-content grey darken-3 white-text">
              <button
                @click="product.total++"
                class="button btn-small halfway-fab waves-effect waves-light red"
              >
                <i class="material-icons">add</i>
              </button>
              <button
                v-if="product.total > 0"
                @click="product.total--"
                class="button btn-small halfway-fab waves-effect waves-light red"
              >
                <i class="material-icons">remove</i>
              </button>
              <br />
              Price: {{ product.price }}
            </div>
          </div>
        </div>
      </div>
    </div>
    <div v-show="showCar" class="container">
      <h2>Shopping Car</h2>
      <table class="responsive-table">
        <thead>
          <th>Name</th>
          <th>Quantity</th>
          <th>Subtract</th>
          <th>Price</th>
        </thead>
        <tbody>
          <tr v-for="product in Allproducts">
            <template v-if="product.total > 0">
              <td>{{ product.name }}</td>
              <td>{{ product.total }}</td>
              <td>
                <button
                  v-if="product.total > 0"
                  @click="product.total--"
                  class="button btn-small halfway-fab waves-effect waves-light red"
                >
                  <i class="material-icons">remove</i>
                </button>
              </td>
              <td>{{ product.price * product.total }}</td>
            </template>
          </tr>
        </tbody>
      </table>
      <div>
        <p>{{ totalPrice }}</p>
      </div>
      <button
        @click="
          showCar = false;
          buyAgain = true;
        "
      >
        Ver productos
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "products",
  data() {
    return {
      showCar: false,
      buyAgain: true,
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
          image: "/assets/shapes.webp",
        },
        {
          name: "wowcube",
          price: 1838000,
          total: 0,
          image: "/assets/wowcube-preview.jpg",
        },
      ],
    };
  },
  computed: {
    sumProducts() {
      let quantityProducts = 0;
      this.Allproducts.forEach((product) => {
        quantityProducts += product.total;
      });
      return quantityProducts;
    },
    totalPrice() {
      let toPay = 0;
      this.Allproducts.forEach((product) => {
        toPay += product.price * product.total;
      });
      return toPay;
    },
  },
};
</script>
<style scoped>
.button {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  margin-left: 5px;
}
.button i {
  margin-right: 10px;
  padding-right: 10px;
}
</style>
