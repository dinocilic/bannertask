<template >
  <div class="container-fluid ">
    <div class="header">
      <div class="topbar">
        <ul class="nav justify-content-end">
          <li class="nav-items"><a href="#" class="nav-link"> Home </a></li>
          <li class="nav-items"><a href="#about" class="nav-link"> About </a></li>
          <li class="nav-items"><a href="#banner" class="nav-link"> Banner </a></li>
        </ul>
      </div>
      <div class="jumbotron">
        <h2 class="text-center">
          {{ msg }}
        </h2>
      </div>
    </div>
  
    <div class="slideshow">
      <div id="banner" class="carousel slide" data-ride="carousel" data-pause="false" data-interval="3000">
        <ol class="carousel-indicators">
          <li data-target="#banner" data-slide-to="0" class="active indicator"></li>
          <li data-target="#banner" data-slide-to="1" class="indicator"></li>
          <li data-target="#banner" data-slide-to="2" class="indicator"></li>
          <li data-target="#banner" data-slide-to="3" class="indicator"></li>
          <li data-target="#banner" data-slide-to="4" class="indicator"></li>
          <li data-target="#banner" data-slide-to="5" class="indicator"></li>
        </ol>
          <div class="carousel-inner">
            <div class="carousel-item" v-for="(ban, idx) in banners" :key="ban.id" :class="{ active: idx == 0 }">
              <img :src="ban['FullImageUrl']" class="img-fluid" alt="...">
            </div>
          </div>
        <a class="carousel-control-prev" href="#banner" role="button" data-slide="prev">
          <span class="carousel-control-prev-icon" aria-hidden="true"></span>
          <span class="sr-only">Previous</span>
        </a>
        <a class="carousel-control-next" href="#banner" role="button" data-slide="next">
          <span class="carousel-control-next-icon" aria-hidden="true"></span>
          <span class="sr-only">Next</span>
        </a>
      </div>
    </div>

    <div id="about" class="row info no-gutters justify-content-center">
      
      <div class="col-sm-12 col-md-12 col-lg-6 col-xl-6 banner-info">
        <div class="card">
          <div class="card-header">
            <h3 class="text-center"> Simple Banner App</h3>
          </div>
          <div class="card-body">
            <p class="card-text">
              Lorem ipsum dolor sit, amet consectetur adipisicing elit. <br> Debitis asperiores delectus, id consectetur dolores, ipsa assumenda, esse odit officiis voluptatum nihil. Obcaecati impedit reprehenderit unde aliquam cum facilis modi perspiciatis!
            </p>
          </div>
          <div class="card-footer">
          </div>
        </div>
      </div>      
    </div>

  <footer class="footer">
    <div class="row no-gutters">
      <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12 text-center">
        <h4> Dino Čilić </h4>
        <p>&copy All rights reserved </p>
				<blockquote>
					<q class="quote">
						Stay positive, work hard, make it happen.
					</q>
				</blockquote>
      </div>
    </div>
  </footer>

  </div>
</template>

<script>
import axios from 'axios';
import { constants } from 'crypto';

export default {
  name: 'Home',

  data () {
    return {
      banners: [],
      msg: "Banner App",
      url: "https://demo.evona.ba:3100/banners/0",
      testUrl: 'https://jsonplaceholder.typicode.com/users',
      err: ''
    }
  },
  mounted: function () {
    // $(document).ready(function () {
    //   $.ajax({
    //     url: "https://demo.evona.ba:3100/banners/0",
    //     type: "GET",
    //     success: function (response) {
    //       this.banners = response
    //       console.log(response)
    //     },
    //     error: function (errors) {
    //       console.log("Error occured " + errors)
    //     }
    //   })
    // })
    axios.get(this.url, { 'headers': {'TerminalId': 2222}})
      .then(function (response) {
        this.banners = response.data['Result']
        console.log(response.data['Result'])
      }.bind(this))
      .catch(function (error) {
        this.err = error.response
        console.log("Error : " + error.response)
      }.bind(this))
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

.container-fluid {
  padding: 0;
  margin: 0;
}

.nav {
  background-color: #000123;
}
.nav .nav-link {
  color: #f4f4f4f4;
}
.nav .nav-link:hover {
  opacity: .7;
}

.jumbotron {
  background-color: black;
  color: #f4f4f4f4;
  border-radius: 0;
  margin: 0;
}
.jumbotron:hover {
  opacity: .7;
  background-color: #000123;
  letter-spacing: 0.5rem;
  font-weight: bold;
}

.carousel {
  background: #000123;
}
.carousel-inner img {
  height: 300px;
  width: auto;
  margin: auto;
  display: block;
}

.carousel-indicators li {
  height: 20px;
  position: relative;
  left: 35%;
  background-color: white;
}

.row .banner-info {
  margin-top: 3rem;
  margin-bottom: 3rem;
}
.banner-info .card {
  border-radius: 25px;
  padding: 25px;
  background-color: #000123;
   color: #f4f4f4;
}
.banner-info .card:hover {
  opacity: .7;
}

.banner-info .card-text {
  margin: 1rem;
  font-family: 'Times New Roman', Times, serif;
}

.footer {
  font-size: 14px;
  letter-spacing: 1px;
  border-top: 2px solid black;
  background-color: #000123;
  color: #f4f4f4;
}
.footer .row {
  margin-top: 1rem;
}

</style>
