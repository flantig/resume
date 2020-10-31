/*
 *@param template(line 14): templates are not rendered immediately when the page is loaded so I use it to give my site some time to know which panel the user clicked on.
 *If the user clicked on a panel with a specific title, it'll look through and see if that title matches up with any of the titles in data(){ projects: [...] } before
 *loading info for it.
 *
 *    v-for="line in item.body.split('\n')": This is my admittedly janky solution to adding linebreaks into the text being pulled in from data(){ projects: [...] }. When it finds a "/n"
 *    in the text, the br is inserted in between the split.
 */

<template>
  <div id="modalstyle">
    <div id="modalinner">
      <h2 id="title">{{ title }}</h2>

      <div v-for="item in projects" v-bind:key="item.key">
        <template v-if="item.title === title"><h3 id="body" v-for="line in item.body.split('\n')" v-bind:key="line">
          {{ line }} <br></h3></template>
      </div>
      <button @click="respond" class="myButton" id="button">Close</button>

    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",

  data() {
    return {
      projects: [{
        key: 0,
        title: "Full Stack Energy Database",
        body: "The motivation behind this project is to eventually migrate away from excel and to a solution that can process calculations faster while offering valuable analysis at a glance of energy data over time. The current workflow revolves around maintaining gargantuan spreadsheets with over 90,000 rows spanning across multiple worksheets. As a result, calculations can take up to an entire real life minute on average and in worst cases up to 3 minutes."
      },
        {
          key: 1,
          title: "VBA Scripts",
          body: "Analyzing and data processing various representations of data inputs in VBA, Excel, and Python utilizing commonly practiced data structures and libraries (such as pandas, and openpyxl)."
        },
        {
          key: 2,
          title: "Selenium Automation",
          body: "Energy bills are paid as they come in but aren't unfortunately aren't reflected in Energy Cap's systems for up to a month at times. As a result, it is vital to check up on what Energy Cap's database believes is overdue to ensure no late fees are charged. \n \n With a clear motivation in mind, I wrote a script that fetches and dispatches the current billing statement to relevant personnel so that we can monitor 'overdue' bills and bills that are cleared."
        },]
    }
  },
  props: {
    title: String,

  },
  methods: {
    respond() {
      this.$emit('toggle')
    },
  }
}
</script>

<style scoped>
#title {

  text-align: center;
  font-size: 400%;
  color: floralwhite;
  overflow: auto;
}

#body {
  text-align: center;

  color: floralwhite;
  margin-right: 3%;
  margin-left: 3%;
}

#modalinner {
  height: 90%;
  margin: 1em;
  overflow-y: auto;
}

#modalstyle {
  background-color: #444444;
  box-shadow: 5px 5px 1px #ed5c6f;
  position: fixed;
  top: 50%;
  width: 50%;
  min-width: 650px;
  height: 50%;

  scrollbar-width: none;
  border-radius: 20px;
  left: 50%;
  -webkit-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  overflow: auto;
}

#button {
  position: absolute;
  bottom: 2%;
  right: 1%;
}

.myButton {
  background-color: #ed5c6f;
  border-radius: 28px;
  display: inline-block;
  cursor: pointer;
  font-family: Arial;
  font-size: 17px;
  border: 0;
  color: floralwhite;
  padding: 16px 31px;
  text-decoration: none;
}

.myButton:hover {
  background-color: #d17985;

}

.myButton:active {
  position: absolute;
  border-radius: 22px;

}


</style>