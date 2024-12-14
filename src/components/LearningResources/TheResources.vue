<template>
    <BaseCard>
        <BaseButton @click="setSelectedTab('StoredResources')" :mode="storedResButtonMode">StoredResources</BaseButton>
        <BaseButton @click="setSelectedTab('AddResource')" :mode="addResButtonMode">Add Resource</BaseButton>
    </BaseCard>
    <component :is="selectedTab"></component>
	<!-- <StoredResources :resources="storedResources"></StoredResources> -->

</template>

<script>
import AddResource from './AddResource.vue';
import StoredResources from './StoredResources.vue';
export default {
    components:{
        AddResource,
        StoredResources
    },
    data(){
        return{
            selectedTab:'StoredResources',
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
    },
    provide(){
        return{
            resources: this.storedResources
        }
    },
    methods:{
        setSelectedTab(tab){
            this.selectedTab = tab;

        }
    },
    computed:{
        storedResButtonMode(){
            return this.selectedTab === 'StoredResources' ? null : 'flat'
        },
        addResButtonMode(){
            return this.selectedTab === 'AddResource' ? null : 'flat'
        }
    }
}
</script>