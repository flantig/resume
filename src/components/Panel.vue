<template>
  <ul>
    <li id="divstyle" v-for="items in panelItems" v-bind:key="items.title" v-on:click="panelOpener = false">
      <h1 id="h1style">{{ items.title }}</h1>
      <img id="imgStyle" :src="items.src">

    </li>
  </ul>
</template>

<script>

export default {
  name: 'Panel',

  data() {
    return {

    }
  },
  props: {
    panelItems: {
      required: true,
      type: Object
    }
  },
  components: {
  }
}
</script>

<style scoped>
#imgStyle {
  width: 25%;
  left: initial;
  margin-bottom: -.4%;
  border-radius: 10px;
}

#h1style {
  color: floralwhite;
  font-size: 200%;
  align-self: center;
  float: right;
  padding-right: 5%;
}

#divstyle {
  background-color: #444444;
  width: 60%;
  height: auto;
  margin: 0px auto;
  margin-top: 2%;
  border-radius: 10px;
  list-style: none;
}
</style>