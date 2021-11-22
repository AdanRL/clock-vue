<template>
<VueClock theme="blue"></VueClock>
<VueClock></VueClock>
<VueClock theme="green"></VueClock>
</template>

<script>
import VueClock from "./components/VueClock.vue";
export default {

  name: "App",

  components: {

     VueClock: VueClock

  }

}
</script>

<style>
</style>
