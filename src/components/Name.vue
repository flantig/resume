<template>
  <div id="nameStyle">

    <h1 :style="h1stylename">Franklin Lantigua</h1>
    <img v-for="item in logoImages" v-bind:key="item.id" v-bind:src="item.src" alt="Not found"
         v-on:click="item.openTab()" v-on:mousedown="item.imgStyle.opacity = .3"
         v-on:mouseup="item.imgStyle.opacity = 1" :style="item.imgStyle">
  </div>
</template>

<script>

export default {

  name: 'Name',
  data() {
    return {
      h1stylename: {
        color: "floralwhite",
        fontSize: "300%",
        backgroundColor: "#ed5c6f",
        borderRadius: "30px",
        padding: "10px"
      },
      logoImages: [{
        id: 1, src: require("../assets/headerImages/linkedin.webp"), openTab: function () {
          window.open("https://www.linkedin.com/in/franklin-lantigua-06831aba/")
        }, imgStyle: {width: "9%", margin: "5px", opacity: 1, minWidth: "70px"}
      }, {
        id: 2, src: require("../assets/headerImages/pdf.png"), openTab: function () {
          window.open("https://drive.google.com/file/d/164LEDfctEf2hm2lvF91Vrde7i3ThSNwK/view?usp=sharing")
        }, imgStyle: {width: "9%", margin: "5px", opacity: 1, minWidth: "70px"}
      }, {
        id: 3, src: require("../assets/headerImages/gitcat.png"), openTab: function () {
          window.open("https://github.com/flantig")
        }, imgStyle: {width: "9%", margin: "5px", opacity: 1, minWidth: "70px"}
      }]
    }
  },

}
</script>

<style scoped>

#nameStyle {
  text-align: center;

  width: 40%;
  height: auto;
  margin: 0px auto;
  margin-top: 7%;
  border-radius: 50px;
  list-style: none;
  padding-top: 1%;
  padding-bottom: 1%;
  margin-bottom: 9%;
}
</style>