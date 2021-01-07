<template>
  <div id="app">
      <div class="app-container">
          <div class="left-panel">

          </div>
          <div class="right-panel">


          </div>
      </div>

      <!-- Model Name -->
      <div class="name">{{ name }}</div>

      <!-- Hero Image -->
      <div class="hero-img-container">
        <img src="./assets/Capture 2.png" class="hero-image" />
      </div>


      <!-- Social Media Links -->
      <ul class="social-links">
        <li>
          <a :href="instagramLink">
            <img src="./assets/instagram.png"/>
          </a>
        </li>
        <li>
          <a :href="twitterLink">
            <img src="./assets/twitter.png"/>
          </a>
        </li>
        <li>
          <a :href="snapchatLink">
            <img src="./assets/snapchat.png"/>
          </a>
        </li>
        <li>  
          <a :href="emailLink">
            <img src="./assets/email.png"/>
          </a>
        </li>
      </ul>

      <!-- Menu Links -->
      <div class="menu">
        <ul class="menu-links">
          <li>HOME</li>
          <li>ABOUT</li>
          <li><img src="./assets/Capture 1.png"/></li>
          <li>GALLERY</li>
          <li>CONTACT</li>
        </ul>
      </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      name: '',
      twitter: '',
      instagram: '',
      snapchat: '',
      email: ''
    }
  },
  mounted() {
      this.$http.get("https://hirng-x2021.glitch.me/api")
        .then(response => {
            this.name = response.body.name;
            this.twitter = response.body.social_media.twitter;
            this.instagram = response.body.social_media.instagram;
            this.snapchat = response.body.social_media.snapchat;
            this.email = response.body.social_media.email;
      }, error => {
          console.error(error);
      });
  },
  computed: {
    twitterLink: {
      get: function() {
        return `https://twitter.com/${this.twitter}`
      }
    },
    instagramLink: {
      get: function() {
        return `https://www.instagram.com/${this.instagram}`
      }
    },
    snapchatLink: {
      get: function() {
        return `https://www.snapchat.com/add/${this.snapchat}`
      }
    },
    emailLink: {
      get: function() {
        return `mailto:${this.email}`
      }
    }
  }
}
</script>

<style>
  body{
    margin: 0;
    padding: 0;
  }

  #app{
    height: 100vh;
    width: 100%;
  }

  .app-container{
    display: flex;
  }

  .name{
    font-size: 30px;
    letter-spacing: 2px;
    font-weight: lighter;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    color: #fff;
    position: absolute;
    top: 10px;
    text-align: center;
    width: 100%;
  }

  .left-panel{
    height: 100vh;
    width: 50%;
    background-color: #bd0f4d;
  }

  .right-panel{
    height: 100vh;
    width: 55%;
    background-color: #cb2964;
  }

  .social-links{
    position: absolute;
    right: 0;
    top: 26%;
    list-style-type: none;
    margin: 10px;
    padding: 0;
  }

  .social-links img{
    height: 40px;
    padding: 10px;
  }

  .menu-links{
    position: absolute;
    bottom: 0;
    list-style-type: none;
    display: flex;
    padding: 0;
    width: 50%;
    justify-content: space-around;
    align-items: center;
    text-align: center;
    left: 25%;
  }

  .menu-links li{
    font-size: 20px;
    letter-spacing: 2px;
    font-weight: lighter;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    color: #fff;
  }

  .hero-img-container{
    position: absolute;
    top: 10%;
    display: flex;
    justify-content: center;
    align-content: center;
    width: 100%;
  }

  .hero-image{
    max-height: 450px;
    max-width: 90%;
    box-shadow: 1px 0px 18px -5px #000;
  }

  @media only screen and (max-width: 450px) {
    .menu-links{
      flex-direction: column;
    }
    .menu-links li{
      margin-bottom: 2px;
    }
  }
</style>
