<template>
  <div style="position: fixed; z-index: 9;" >

      <div >

        <nav role="navigation" >

          <div id="menuToggle">
            <input type="checkbox" />
            <span></span>
            <span></span>
            <span></span>
            <ul id="menu" v-bind:style="{'background-image': 'url('+BackgroundImage+')'}" >
              <router-link  to="/">
              <li><a class="a" href="#">Home</a></li>
              </router-link>
              <router-link  to="/AboutUs">
              <li><a class="a" href="#">About <br> Us</a></li>
              </router-link>
              <router-link  to="/OurServices">
              <li><a class="a" href="#">Our <br> Services</a></li>
              </router-link>
              <router-link  to="/ContactUs">
              <li><a class="a" href="#">Contact <br> Us</a></li>
              </router-link>
            </ul>
          </div>
        </nav>
      </div>
    </div>

</template>

<script>
    export default {
        name: "HomePageMobile",
      data() {
        return {
          BackgroundImage: require('../assets/images/MobileMenuBackground.png'),
        }
      }

    }
</script>

<style scoped>
  #Logo {

    width: 70%;
    height:12%;
    left: 25%;
    position: absolute;
  }
  .a {
    text-decoration: none;
    color: #1E1E23;
    opacity:1;
    font-family: 'Montserrat', sans-serif;
    font-weight: 400;
    font-size: 1.6em;
    transition: 200ms;
    text-shadow: 0.001em 0.001em forestgreen;
  }
  .a:hover {
    opacity:0.5;
  }
  ul {
    padding: 0;
    list-style-type: none;
  }


  nav {
    background-color: transparent;
    height: 65px;
    position: sticky;
  }


  #menuToggle {
    display: flex;
    flex-direction: column;
    position: relative;
    top: 25px;
    left: 25px;
    z-index: 1;
    -webkit-user-select: none;
    user-select: none;
  }

  #menuToggle input
  {
    display: flex;
    width: 40px;
    height: 32px;
    position: absolute;
    cursor: pointer;
    opacity: 0;
    z-index: 2;
  }

  #menuToggle span
  {
    display: flex;
    width: 29px;
    height: 2px;
    margin-bottom: 5px;
    position: relative;
    background: #859e30;
    border-radius: 3px;
    z-index: 1;
    transform-origin: 5px 0px;
    transition: transform 0.5s cubic-bezier(0.77,0.2,0.05,1.0),
    background 0.5s cubic-bezier(0.77,0.2,0.05,1.0),
    opacity 0.55s ease;
  }

  #menuToggle span:first-child
  {
    transform-origin: 0% 0%;
  }

  #menuToggle span:nth-last-child(2)
  {
    transform-origin: 0% 100%;
  }

  #menuToggle input:checked ~ span
  {
    opacity: 1;
    transform: rotate(45deg) translate(-3px, -1px);
    background: #36383F;
  }
  #menuToggle input:checked ~ span:nth-last-child(3)
  {
    opacity: 0;
    transform: rotate(0deg) scale(0.2, 0.2);
  }

  #menuToggle input:checked ~ span:nth-last-child(2)
  {
    transform: rotate(-45deg) translate(0, -1px);
  }

  #menu
  {
    position: absolute;
    width: 200px;
    height: 100vh;
    box-shadow: 0px 0px 100vw #444444;
    margin: -50px 0 0 -50px;
    padding-left: 20px;
    padding-top: 90px;
    background-color: #F5F6FA;
    -webkit-font-smoothing: antialiased;
    transform-origin: 0% 0%;
    transform: translate(-100%, 0);
    transition: transform 0.5s cubic-bezier(0.77,0.2,0.05,1.0);
    background-repeat: no-repeat;
    background-size: cover;
  }

  #menu li
  {
    padding-top: 30px;
    padding-bottom: 30px;
    transition-delay: 2s;
  }

  #menuToggle input:checked ~ ul
  {
    transform: none;
  }
</style>
