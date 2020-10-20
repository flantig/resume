<template>
<div id="divstyle" >
<h1>Hi</h1>
</div>
</template>

<script>
export default {
name: "Modal",
  props: {

  }
}
</script>

<style scoped>
#divstyle {
  background-color: coral;
  position: fixed;
  top: 50%;
  left: 50%;
  -webkit-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}
</style>