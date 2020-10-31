/*
 * @param img: In this component, I don't pass in any props and all the data it'd use is in data() because there's not too much going on in this component that
 * would even require props to be passed down.
 *
 *      v-on:click - when one of the three icons (linkedin, pdf drive, or github) are clicked it'll send you to it's respective page as noted in logoImages
 *
 *      v-on:mousedown/mouseup: I figured the user should get some feedback when interacting with the site even if it's minimal. Upon mousedown, the opacity of the image button
 *      is reduced to indicate that it is indeed being touched. This is also the reason why I added the styling to data() and not in style because manipulating it otherwise would mean
 *      implementing an active tag for CSS like I did in the Panel component and hover.
 */

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
        textAlign: "center",
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
  min-width: 400px;
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