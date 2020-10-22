<template>

  <section>
    <teleport>
      <transition name="fade" >
        <Modal v-if="panelOpener" :title="propTitle" @toggle="off"/>
      </transition>
    </teleport>

    <ul>
      <li class="container" v-for="(items) in panelItems" v-bind:key="items.title"
          @click="toggleModal(items.title)" >

        <div class="header-1">
          <h1 id="h1style">{{ items.title }}</h1>
        </div>
        <div class="header-0">
          <img id="imgStyle" :src="items.src">
        </div>
        <div class="right">
          <img v-for="tech in items.technology" v-bind:key="tech.index" id="technology" :src="tech">
        </div>

      </li>
    </ul>
  </section>
</template>

<script>

import Modal from "@/components/Modal";

export default {
  name: 'Panel',
  data() {
    return {
      panelOpener: false,
      propTitle: "Taco",
      hovering: false
    }
  },
  props: {
    panelItems: {
      required: true,
      type: Object
    }
  },
  components: {
    Modal
  },
  methods: {
    toggleModal: function (key) {
      this.panelOpener = !this.panelOpener;
      this.propTitle = key;
    },
    off: function (){
      this.panelOpener = false;
    },
  }
}
</script>

<style scoped>
#imgStyle {
  width: 72%;
  min-width: 200px;
  border-radius: 10px;
}

#h1style {
  color: floralwhite;

  font-size: 250%;
  text-align: right;
  right: initial;
  overflow: auto;
}


#technology {
  width:  10%;
  min-width: 50px;
  float: right;
  overflow: auto;
}

/**
  Below is the grid container, to see the layout of the grid and its borders use the following block of code for a dotted outline.

.container > div {
  border: 1px dashed #d85151;
}

  If you ever need to make a new grid, visit https://vue-grid-generator.netlify.app It's an absolute life saver and will help you generate grids.

 header-0: The image representing the project
 header-1: The title of the project
 right: The technology you're using (React, JS, Python, etc.)
 */

.container {
  display: grid;
  width: 60%;
  height: auto;
  grid-template-areas: "header-0 header-1"
  "header-0 right";
  grid-template-columns: .4fr 1fr;
  grid-template-rows: .5fr 1fr;
  background-color: #444444;
  margin: 0px auto; /*centers the container*/
  margin-top: 2%; /*it's what divides it from the other panels*/
  border-radius: 10px; /*Rounds the edges*/
  list-style: none; /*removes the bullet points from the list*/
  box-shadow: 5px 5px 1px #ed5c6f;
}

.container:hover{
  background-color: #676767;
}

.header-0 {
  grid-area: header-0;

  margin-top: 25%;
  margin-bottom: -1.5%;

}

.header-1 {
  grid-area: header-1;
  min-width: 70%;


}

.right {
  grid-area: right;
  padding-top: 1%;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s ease !important;
}

.fade-enter, .fade-leave-to {
  opacity: 0 !important;
}
</style>