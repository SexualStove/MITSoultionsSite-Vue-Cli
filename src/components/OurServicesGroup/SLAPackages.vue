<template>
    <div style="background-color: #dadbe0; padding-bottom: 100px">
      <h1 class="SectionTitle"> Service Level Agreements (SLA) </h1>
      <div style="width: 100%; height: 10vw"></div>
      <transition name="PackageAniLeft" :key="Packages">
        <div id="PackageBronze" v-if="Packages" style="" class="Package">
          <div style="background-color: #cdced3;">
            <h1 class="PackageTitle" style=" text-shadow: #F7C59F 2.5px 1.5px"> Bronze </h1>
            <h4 class="PackageSubTitle">Understand Whats Going On</h4>
          </div>
          <div class="PackageInfo">
            <h4 class="PackageFeature"> Proactive monitoring </h4>
            <div class="Line"></div>
            <h4 class="PackageFeature"> Formalised system status reporting </h4>
          </div>
        </div>
      </transition>
      <div id="Gold" class="Package">
        <div style="background-color: #cdced3;">
          <h1 class="PackageTitle" style="text-shadow: #E1CE7A 2.5px 1.5px"> Gold </h1>
          <h4 class="PackageSubTitle">Full 24/7 Support</h4>
        </div>
        <div class="PackageInfo">
          <h4 class="PackageFeature"> Silver Plus+</h4>
          <div class="Line"></div>
          <h4 class="PackageFeature"> 24/7 break/fix support </h4>
          <div class="Line"></div>
          <h4 class="PackageFeature"> Agreed response times </h4>
          <div class="Line"></div>
          <h4 class="PackageFeature"> Formalised disaster recovery planning </h4>

        </div>
      </div>
      <transition name="PackageAniRight" :key="Packages">
        <div v-if="Packages" id="PackageSliver" style="" class="Package">
          <div style="background-color: #cdced3;">
            <h1 class="PackageTitle" style="text-shadow: #D8DBE2 2.5px 1.5px"> Silver </h1>
            <h4 class="PackageSubTitle">Critical Support</h4>
          </div>
          <div class="PackageInfo">
            <h4 class="PackageFeature"> Bronze Plus+</h4>
            <div class="Line"></div>
            <h4 class="PackageFeature"> Proactive monitoring </h4>
            <div class="Line"></div>
            <h4 class="PackageFeature"> Formalised system status reporting </h4>

          </div>
        </div>
      </transition>

      <div class="BreakFix">
        <div class="BreakFixContent">
          <h1 class="BreakFixIntro"> For more flexibility or as a supplement to our plans, we have <br></h1>
          <div class="ServiceDiv_SLA" style="position: relative; margin: auto" @click="ServiceClick(1)">
            <div class="IconBottomRight"></div>
            <div class="IconBottomLeft"></div>
            <div class="IconTopRight"></div>
            <div class="IconTopLeft"></div>
            <h1 class="BreakFixTitle"> Break/Fix Support </h1>
          </div>
      </div>
      </div>
    </div>
</template>

<script>

  import {EventBus} from "../../App";
  import JQuery from 'jquery';
  let $ = JQuery;
    export default {
        name: "SLAPackages",
      data () {
        return {
          Packages: false,
          ReadMoreArray: [
            {ReadBool: false, TransitionBool: "Divder1", Line: "Line1", Arrow: "Arrow1", DaddyNode: "#ItemOne", Top: 150},
            {ReadBool: false, TransitionBool: "Divder2", Line: "Line2", Arrow: "Arrow2", DaddyNode: "#ItemTwo", Top:-300},
            {ReadBool: false, TransitionBool: "Divder3", Line: "Line3", Arrow: "Arrow3", DaddyNode: "#ItemThree", Top: -300},
            {ReadBool: false, TransitionBool: "Divder4", Line: "Line4", Arrow: "Arrow4", DaddyNode: "#ItemFour", Top: -300}
          ]
        }
      },
      mounted() {
        var self = this;

        EventBus.$on('MobileSize', changed => {
          console.log(`Packages managed to get: ${changed} `);
          self.Packages = changed;
        });
        window.onload = EventBus.$emit('PageLoaded', true);

        this.$nextTick(function(){
          window.addEventListener("scroll", function(){
            self.Scrolled = document.documentElement.scrollTop;
             if(document.documentElement.scrollTop >= 800) {
               self.Packages = true;
            }


          })
        })
      },

      methods: {
        ServiceClick(Int) {
          $('html, body').animate({
            scrollTop: $(this.ReadMoreArray[Int].DaddyNode).offset().top + this.ReadMoreArray[Int].Top
          }, 2000);
        }
      }


    }
</script>

<style scoped>

  h4 {
    font-family: 'Montserrat', sans-serif;
    font-weight: 400;
    font-size: 1.2vw;
    padding: 5px;
  }

  .BreakFix {

    padding-top: 100px;
    width: 100%
  }
  .BreakFixContent {
    background-color: #d6d7dc;
  }

 .PackageFeature {
   text-align: center;
   font-family: 'Montserrat', sans-serif;
   font-weight: 400;
   font-size: 24px;
   padding: 20px 5px 20px 5px;
   color: #495d68;
   margin-bottom: initial;
 }
  .PackageSubTitle {
    font-size: 28px;
  }
 .Line {
   width: 80%;
   background-color: whitesmoke;
   height: 1px;
   margin-left: 10%;
   margin-top: initial;
 }
.PackagePrice {
  width: 100%;
  font-size: 1.5vw;
  font-family: 'Bebas Neue', cursive;
  color: #495d68;
}
.PackageTitle {
  width: 100%;
  font-family: 'Bebas Neue', cursive;
  color: #495d68;
  font-size: 3.5vw;

}

 .Package {
   display: inline-block;
   width: 25%;
   position: relative;
   z-index: 0;
   box-shadow: 0px 0px 20px #888888;
   transition: 0.8s;
   border-radius: 20px;
 }
 .Package:hover {
   transform: scale(1.05, 1.05);
   z-index: 3;
 }
 .PackageInfo {
   background-color: #d6d7dc; margin-top: -10px;
   padding: 50px;
   border-bottom-left-radius: 20px;
   border-bottom-right-radius: 20px;
 }

.SectionTitle {
  width: 100%;
  padding-left: 40px;
  padding-bottom: 60px;
  font-family: 'Bebas Neue', cursive;
  font-weight: 400;
  font-size: 80px;
  color: #495d68;
  position: relative;
  float: left;
  text-align: left;
  border-bottom: 3px dotted dimgray;
}
.BreakFixIntro {
  font-family: 'Bebas Neue', cursive;
  font-weight: 400;
  font-size: 40px;
  color: #495d68;
}
.BreakFixTitle {
  font-family: 'Bebas Neue', cursive;
  font-weight: 400;
  font-size: 50px;
  color: #495d68;
}

  #Gold {
    border-bottom:solid 2px gold;
    z-index: 1;
  }
  #PackageBronze {
    margin-left: 10%;
    border-bottom:solid 2px #F7C59F;
  }
  #PackageSliver {
    margin-right: 10%;
    border-bottom:solid 2px #D8DBE2;
  }


 .PackageAniRight-enter-active, .PackageAniRight-leave-active {
   transition: all .5s;
 }
 .PackageAniLeft-enter-active, .PackageAniLeft-leave-active {
   transition: all .5s;
 }
 .PackageAniRight-enter, .PackageAniRight-leave-to /* .fade-leave-active below version 2.1.8 */ {
   transform: translateX(-50%);
   opacity: 0;
 }
 .PackageAniLeft-enter, .PackageAniLeft-leave-to /* .fade-leave-active below version 2.1.8 */ {
   transform: translateX(50%);
   opacity: 0;
 }

  .IconBottomRight {
    transition: 0.7s;
    position: absolute;
    border-bottom: 2px solid #859e30;
    border-right: 2px solid #859e30;
    height: 5%;
    width: 3%;
    bottom: 0;
    right: 0;
  }
  .IconBottomLeft {
    transition: 0.7s;
    position: absolute;
    border-bottom: 2px solid #859e30;
    border-left: 2px solid #859e30;
    height: 5%;
    width: 3%;
    bottom: 0;
    left: 0;
  }
  .IconTopRight {
    transition: 0.7s;
    position: absolute;
    border-top: 2px solid #859e30;
    border-right: 2px solid #859e30;
    height: 5%;
    width: 3%;
    top: 0;
    right: 0;
  }
  .IconTopLeft {
    transition: 0.7s;
    position: absolute;
    border-top: 2px solid #859e30;
    border-left: 2px solid #859e30;
    height: 5%;
    width: 3%;
    top: 0;
    left: 0;
  }

  .ServiceDiv_SLA {
    z-index: 3;
    display: inline-block;
    padding: 10px 5px 0px 5px;
    margin-bottom: -5px;
    transition: 1s;
  }

  .ServiceDiv_SLA:hover {
    background: rgba(100%, 100%, 100%, 0.2);
    cursor: pointer;
    transform: scale(1.05, 1.05);
  }

  .ServiceDiv_SLA:hover .IconTopLeft {
    height: 50%;
    width: 50%;
  }
  .ServiceDiv_SLA:hover .IconTopRight {
    height: 50%;
    width: 50%;
  }
  .ServiceDiv_SLA:hover .IconBottomLeft {
    height: 50%;
    width: 50%;
  }
  .ServiceDiv_SLA:hover .IconBottomRight {
    height: 50%;
    width: 50%;
  }
  @media (max-width:800px){
    .PackageSubTitle {
      font-size: 22px;
    }
    .PackageFeature {
      font-size: 20px;
    }
    .PackageInfo {
      padding: 20px;
    }
    .PackageTitle {
      font-size: 13vw;
    }

    #PackageBronze {
      margin-left: 0
    }
    #PackageSliver {
      margin-right: 0
    }
    .Package {
      width: 30%;
    }
    .SectionTitle {
      width: 100%;
      padding-top: 20px;
      padding-left: 0px;
      padding-bottom: 60px;
      font-family: 'Bebas Neue', cursive;
      font-weight: 400;
      font-size: 13vw;
      color: #495d68;
      position: relative;
      float: none;
      text-align: center;
      border-bottom: 3px dotted dimgray;
    }
    @media (max-width:600px){
      .Package {
        width: 90%;
        margin: 5%;
      }
      #PackageBronze {
        margin-left: 5%
      }
      #PackageSliver {
        margin-right: 5%
      }
    }
  }

</style>
