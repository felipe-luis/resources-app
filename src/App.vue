<template>
	<ul>
		<LearningResource v-for="resource in storedResources" :key="resource"
							:title="resource.title"
							:description="resource.description"
							:link="resource.link"></LearningResource>
	</ul>
</template>

<script>
import LearningResource from './components/LearningResources/LearningResource.vue';
export default{
	components:{
		LearningResource
	},
	data(){
		return{
			storedResources: [
				{
					id: 'official-guide',
					title: 'Official Guide',
					description: 'The official Vue.js documentation',
					link: 'https://vuejs.org'
				},
				{
					id: 'google',
					title: 'Google',
					description: 'Learn to Google',
					link: 'https://google.com'
				}
			]
		}
	}
}
</script>