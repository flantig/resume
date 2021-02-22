/*@param panelItems: passes in panel data so that the panels know what to load up. Eventually I'm going to pass it to a mobile profile Panel component when I get around
 *to touching up the site.
 *
 *
 */

<template>
  <section id="app">
    <Name/>
    <Panel :panelItems="panelItems"/>

  </section>
</template>

<script>


import Panel from "@/components/Panel";
import Name from "@/components/Name";



export default {
  name: 'App',
  data() {
    return {
      panelItems: [
        {
          title: "Full Stack Energy Database",
          src: require("./assets/panelImages/owl.png"),
          technology: [require("./assets/technologies/pyth.png"), require("./assets/technologies/js.png"), require("./assets/technologies/react.png"), require("./assets/technologies/postnode.png")],
          open: false
        },
        {
          title: "VBA Scripts",
          src: require("./assets/panelImages/vbascript.png"),
          technology: [require("./assets/technologies/excel.png"), require("./assets/technologies/vba.png")],
          open: true
        },
        {
          title: "AniDay",
          src: require("./assets/panelImages/dandyguy.png"),
          technology: [require("./assets/technologies/dis.png"), require("./assets/technologies/js.png")],
          open: false
        },
        {
          title: "WPF Scheduler",
          src: require("./assets/panelImages/scheduler.png"),
          technology: [require("./assets/technologies/csharp.png"),require("./assets/technologies/wpf.png")],
          open: false
        },
        {
          title: "Selenium Automation",
          src: require("./assets/panelImages/selenium.png"),
          technology: [require("./assets/technologies/pyth.png")],
          open: false
        },
        {
          title: "Portfolio",
          src: require("./assets/panelImages/pc.png"),
          technology: [require("./assets/technologies/vue.png"),require("./assets/technologies/htmlcss.png")],
          open: false
        },


      ]
    }
  },
  components: {
    Name,
    Panel,
  }
}
</script>

<style>
html {
  height: 100%
}

body {
  margin: 0;
  padding: 0;
  height: 100%;
  background-color: #222222;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  width: 100%;
  height: 100%;
}
</style>
