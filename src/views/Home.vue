<template>
  <div>
    <Navbar/>
    <div class="gallery">
        <div v-for="product in products" :key="product.id" class="content">
          <img :src="product.image_url">
          <h3><span v-if="product.liked"><i class="fa fa-heart" style="color:red" aria-hidden="true"></i></span> {{product.name}}</h3>
          <!-- <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p> -->
          <h6>Rp. {{numberWithCommas(product.price)}}</h6>
          <!-- <ul>
            <li v-if="product.liked"><i class="fa fa-heart" style="color:red" aria-hidden="true"></i></li>
            <li><i class="fa fa-star" aria-hidden="true"></i></li>
            <li><i class="fa fa-star" aria-hidden="true"></i></li>
            <li><i class="fa fa-star" aria-hidden="true"></i></li>
            <li><i class="fa fa-star" aria-hidden="true"></i></li>
          </ul> -->
          <div class="d-flex">
            <button @click="wishlist(product.id)" class="buy-2">&#x2665; Wishlist</button>
            <button @click="addToCart(product.id)" class="buy-1">Add to Cart</button>
          </div>
        </div>
        <!-- <div class="content">
          <img src="https://rukminim1.flixcart.com/image/416/416/jy0frm80/bag/x/y/e/cute-pink-kitty-girl-mini-bag-gremy-10-original-imafg3bsn976gyg9.jpeg?q=70">
          <h3>Earphone</h3>
          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
          <h6>$40.00</h6>
          <ul>
            <li><i class="fa fa-star" aria-hidden="true"></i></li>
            <li><i class="fa fa-star" aria-hidden="true"></i></li>
            <li><i class="fa fa-star" aria-hidden="true"></i></li>
            <li><i class="fa fa-star" aria-hidden="true"></i></li>
            <li><i class="fa fa-star" aria-hidden="true"></i></li>
          </ul>
          <button class="buy-2">Buy Now</button>
        </div>
        <div class="content">
          <img src="https://rukminim1.flixcart.com/image/416/416/jy0frm80/bag/x/y/e/cute-pink-kitty-girl-mini-bag-gremy-10-original-imafg3bsn976gyg9.jpeg?q=70">
          <h3>Watch</h3>
          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
          <h6>$70.84</h6>
          <ul>
            <li><i class="fa fa-star" aria-hidden="true"></i></li>
            <li><i class="fa fa-star" aria-hidden="true"></i></li>
            <li><i class="fa fa-star" aria-hidden="true"></i></li>
            <li><i class="fa fa-star" aria-hidden="true"></i></li>
            <li><i class="fa fa-star" aria-hidden="true"></i></li>
          </ul>
          <button class="buy-3">Buy Now</button>
        </div> -->
      </div>
  </div>
</template>

<script>
import Navbar from '../components/Navbar.vue'
export default {
  components: { Navbar },
  name: 'Home',
  created () {
    this.getAll()
  },
  // updated () {
  //   this.getAll()
  // },
  computed: {
    products () {
      return this.$store.state.products
    }
  },
  methods: {
    getAll () {
      this.$store.dispatch('getAll')
      this.$store.dispatch('getKeranjang')
    },

    addToCart (id) {
      this.$store.dispatch('addToCart', id)
    },

    numberWithCommas (x) {
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
    },

    wishlist (id) {
      this.$store.dispatch('wishlist', id)
      this.getAll()
    }
  }
}
</script>

<style type="text/css">
  body{
  margin: 0;
  font-family:Nunito Sans;
  }
  h3{
  text-align: center;
  font-size: 30px;
  margin: 0;
  padding-top: 10px;
  }
  a{
  text-decoration: none;
  }
  .gallery{
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  justify-content: center;
  align-items: center;
  margin: 50px 0;
  }
  .content{
  background-color: white;
  width: 24%;
  margin: 15px;
  box-sizing: border-box;
  float: left;
  text-align: center;
  border-radius:10px;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 10px;
  padding-top: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  transition: .4s;
  }
  .content:hover{
  box-shadow: 0 0 11px rgba(33,33,33,.2);
  transform: translate(0px, -8px);
  transition: .6s;
  }
  img{
  width: 200px;
  height: 200px;
  text-align: center;
  margin: 0 auto;
  display: block;
  }
  p{
  text-align: center;
  color: #b2bec3;
  padding: 0 8px;
  }
  h6{
  font-size: 26px;
  text-align: center;
  color: #222f3e;
  margin: 0;
  }
  ul{
  list-style-type: none;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0px;
  }
  li{
  padding: 5px;
  }
  .fa{
  color: #ff9f43;
  font-size: 26px;
  transition: .4s;
  }
  .fa:hover{
  transform: scale(1.3);
  transition: .6s;
  }
  button{
  text-align: center;
  font-size: 24px;
  color: #fff;
  width: 100%;
  padding: 15px;
  border:0px;
  outline: none;
  cursor: pointer;
  margin-top: 5px;
  border-bottom-right-radius: 10px;
  border-bottom-left-radius: 10px;
  }
  .buy-1{
  background-color: #2183a2;
  }
  .buy-2{
  background-color: #3b3e6e;
  }
  .buy-3{
  background-color: #0b0b0b;
  }
  @media(max-width: 1000px){
  .content{
  width: 46%;
  }
  }
  @media(max-width: 750px){
  .content{
  width: 100%;
  }
  }
</style>
