<template>
	<TheHeader title="RememberMe"/>
	<TheResources></TheResources>
</template>

<script>
import TheResources from './components/LearningResources/TheResources.vue';
import TheHeader from './components/layouts/TheHeader.vue';
export default{
	components:{
		TheHeader,
		TheResources
	},
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
  padding: 0;
}
</style>