<template>
  <div>
    <nav>
      <div class="container">
        <ul class="navbar-left">
          <li><router-link to="/">Home</router-link></li>
        </ul> <!--end navbar-left -->

        <ul class="navbar-right">
          <li><a href="#" id="cart"><i class="fa fa-shopping-cart"></i> Cart <span class="badge">{{totalQty}}</span></a></li>
          <!-- <li><a href="#about">Logout</a></li> -->
          <li @click="logout"><router-link to="Login">Logout</router-link></li>
        </ul> <!--end navbar-right -->
      </div> <!--end container -->
    </nav>
    <div class="container">
      <div class="shopping-cart" style="display:none">
        <div class="shopping-cart-header">
          <!-- <i class="fa fa-shopping-cart cart-icon"></i><span class="badge">{{totalQty}}</span> -->
          <!-- <div class="shopping-cart-total"> -->
            <!-- <span class="lighter-text">Total:</span> -->
            <!-- <span class="main-color-text">$2,229.97</span> -->
          <!-- </div> -->
        </div> <!--end shopping-cart-header -->

        <ul>
          <li v-for="cart in carts" :key="cart.id" class="clearfix">
            <!-- <img :src="cart.Product.image_url" /> -->
            <span class="item-name">{{cart.Product.name}}</span>
            <span class="item-quantity">{{cart.quantity}}</span>
          </li>
          <!-- <li class="clearfix">
            <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/195612/cart-item2.jpg" alt="item1" />
            <span class="item-name">KS Automatic Mechanic...</span>
            <span class="item-price">$1,249.99</span>
            <span class="item-quantity">Quantity: 01</span>
          </li>
          <li class="clearfix">
            <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/195612/cart-item3.jpg" alt="item1" />
            <span class="item-name">Kindle, 6" Glare-Free To...</span>
            <span class="item-price">$129.99</span>
            <span class="item-quantity">Quantity: 01</span>
          </li> -->
        </ul>

        <button @click="$router.push('/editcart')" class="button">Edit Cart</button>
      </div> <!--end shopping-cart -->
    </div> <!--end container -->
  </div>
</template>

<script>
import $ from 'jquery'
export default {
  name: 'Navbar',
  computed: {
    carts () {
      return this.$store.state.cart
    },
    cartQty () {
      return this.$store.state.cart.length
    },

    totalQty () {
      return this.$store.state.totalCart
    }
  },
  created () {
    console.log(this.$store.state.cart.length)
  },
  methods: {
    logout () {
      localStorage.removeItem('access_token')
      this.$router.push('/login')
    }
  },
  mounted () {
    $('#cart').on('click', function () {
      $('.shopping-cart').fadeToggle('fast')
    })
  }
}
</script>

<style>
@import url(https://fonts.googleapis.com/css?family=Lato:300,400,700);
@import url(https://maxcdn.bootstrapcdn.com/font-awesome/4.4.0/css/font-awesome.min.css);
*, *:before, *:after {
  box-sizing: border-box;
}

body {
  font: 14px/22px "Lato", Arial, sans-serif;
  background: #6394F8;
}

.lighter-text {
  color: #ABB0BE;
}

.main-color-text {
  color: #6394F8;
}

nav {
  padding: 20px 0 40px 0;
  background: #F8F8F8;
  font-size: 16px;
}
nav .navbar-left {
  float: left;
}
nav .navbar-right {
  float: right;
}
nav ul li {
  display: inline;
  padding-left: 20px;
}
nav ul li a {
  color: #777777;
  text-decoration: none;
}
nav ul li a:hover {
  color: black;
}

.container {
  margin: auto;
  width: 80%;
}

.badge {
  background-color: #6394F8;
  border-radius: 10px;
  color: white;
  display: inline-block;
  font-size: 12px;
  line-height: 1;
  padding: 3px 7px;
  text-align: center;
  vertical-align: middle;
  white-space: nowrap;
}

.shopping-cart {
  margin: 20px 0;
  float: right;
  background: white;
  width: 320px;
  position: relative;
  border-radius: 3px;
  padding: 20px;
}
.shopping-cart .shopping-cart-header {
  border-bottom: 1px solid #E8E8E8;
  padding-bottom: 15px;
}
.shopping-cart .shopping-cart-header .shopping-cart-total {
  float: right;
}
.shopping-cart .shopping-cart-items {
  padding-top: 20px;
}
.shopping-cart .shopping-cart-items li {
  margin-bottom: 18px;
}
.shopping-cart .shopping-cart-items img {
  float: left;
  margin-right: 12px;
}
.shopping-cart .shopping-cart-items .item-name {
  display: block;
  padding-top: 10px;
  font-size: 16px;
}
.shopping-cart .shopping-cart-items .item-price {
  color: #6394F8;
  margin-right: 8px;
}
.shopping-cart .shopping-cart-items .item-quantity {
  color: #ABB0BE;
}

.shopping-cart:after {
  bottom: 100%;
  left: 89%;
  border: solid transparent;
  content: " ";
  height: 0;
  width: 0;
  position: absolute;
  pointer-events: none;
  border-bottom-color: white;
  border-width: 8px;
  margin-left: -8px;
}

.cart-icon {
  color: #515783;
  font-size: 24px;
  margin-right: 7px;
  float: left;
}

.button {
  background: #6394F8;
  color: white;
  text-align: center;
  padding: 12px;
  text-decoration: none;
  display: block;
  border-radius: 3px;
  font-size: 16px;
  margin: 25px 0 15px 0;
}
.button:hover {
  background: #729ef9;
}

.clearfix:after {
  content: "";
  display: table;
  clear: both;
}
</style>
