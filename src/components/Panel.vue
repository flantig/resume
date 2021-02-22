/**
  *@param teleport: the teleport is supposed to target a model in a completely different div in index but it is not implemented properly because for whatever reason it's not targetting
  *#modals in index.html. See th following link for how I tried to implement it:
  *
  *               https://www.youtube.com/watch?v=TYcNDRav-N4&t=287s
  *
  *         Modal: If you're familiar with other frontend frameworks, you'll know that in general props are usually passed down in one direction.
  *
  *               For example- parent -> child1 -> child2 -> child3
  *
  *         But if you're also familiar with frontend frameworks, you'll also know that they added some kind of functionality that lets you communicate with the parent
  *         in some shape or form. In Vue js, the have something called "events." Events basically allow your child component to ping the parent component to do something and is triggered
  *         using some keyword.
  *
  *         In this case it's: @toggle="off"
  *
  *         The Modal component has a function called respond() that pings the toggle event in the Panel component. When Panel is pinged, it uses the function that it is told to use
  *         for this event. In this case, it's off().
  *
  *@param ul: This is the list that will display all of the panels, if someone decides to scrape my site for whatever reason it should be extremely easy to grab what you need.
  *
  *
  *@param li:
  *         panelItems - Are the props that are passed in from App.vue. If this resume were designed with a backend incorporated with it, we wouldn't have any props being passed down from
  *         a json inside of the project itself but this is mean't to be a very simple and barebones resume. If reworked, you'll probably be doing some mounting or async handling
  *
  *         toggleModal - toggles the modal that pops-up upon clicking a panel, there's some more info on that in regards to event handling under teleport above.
  *
  *
  */

<template>


  <section>
    <teleport>
      <transition name="fade">
        <Modal v-if="panelOpener" :title="propTitle" @toggle="off"/>
      </transition>
    </teleport>

    <ul>
      <li class="container" v-for="(items) in panelItems" v-bind:key="items.title"
          @click="toggleModal(items.title)">

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
    off: function () {
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
  width: 10%;
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

 The container has a default min-width of 750px so that it doesn't squish and destroy the panel's layout. So it'll continue to resize until it hits that min-width. The objective will be
 to add a proper mobile version of the site depending on the user but for now this works and isn't jank looking.

 container.hover: was my quick and cheap solution to solving user interaction with the site. Instead of manipulating the CSS from an event, I just added a CSS tag that recognizes mouse hover
 and changes the background of any one particular panel.
 */

.container {
  display: grid;
  width: 60%;
  min-width: 750px;
  height: auto;
  grid-template-areas: "header-0 header-1"
  "header-0 right";
  grid-template-columns: .4fr 1fr;
  grid-template-rows: .5fr 1fr;
  background-color: #444444;
  margin: 0px auto; /*centers the container*/
  margin-bottom: 2%;
  border-radius: 10px; /*Rounds the edges*/
  list-style: none; /*removes the bullet points from the list*/
  box-shadow: 5px 5px 1px #ed5c6f;
}

.container:hover {
  background-color: #676767;
}

.header-0 {
  grid-area: header-0;
  margin-top: 25%;
  margin-bottom: -1.5%;

}

.header-1 {
  grid-area: header-1;
  min-width: 80%;


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