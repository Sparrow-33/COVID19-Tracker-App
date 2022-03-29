<template>
  <HeaderComp title="COVID-19 Tracker"/>
  <div class="container mx-auto">

    <router-view/>
  </div>
</template>

<script>
import HeaderComp from "@/components/HeaderComp";

export default {
  name: 'App',
  components: {
    HeaderComp
  }
}
</script>

<style>

</style>
