<template>
    <BaseDialog v-if="inputIsInvalid" title="Invalid Input" @close="confirmError">
        <template v-slot:default>
            <p>Unfortunately, at least one input value is invalid!</p>
            <p>Please, check all inputs and make sure you enter at least a few charracters into input field!</p>
        </template>
        <template #actions>
            <BaseButton @click="confirmError">Okay</BaseButton>
        </template>
    </BaseDialog>
    <BaseCard @submit.prevent ="submitData">
        <form>
            <div class="form-control">
                <label for="title">Title</label>
                <input id="title" name="title" type="text" v-model="titleInput">
            </div>
            <div class="form-control">
                <label for="description">Description</label>
                <textarea name="description" id="description" rows="3" v-model="descriptionInput"></textarea>
            </div>

            <div class="form-control">
                <label for="link">Link</label>
                <input id="link" name="link" type="url" v-model="linkInput">
            </div>
            <div>
                <BaseButton type="submit">Add Resource</BaseButton>
            </div>
        </form>
    </BaseCard>
</template>

<script>
export default{
    data(){
        return{
            titleInput:'',
            descriptionInput:'',
            linkInput: '',
            inputIsInvalid: false
        }
    },
    methods:{
        submitData(){

            if(this.titleInput.trim() === '' || this.descriptionInput.trim() === '' || this.linkInput.trim() === ''){
                return this.inputIsInvalid = true;
            }

            this.addResource(this.titleInput, this.descriptionInput, this.linkInput);
            this.titleInput = '';
            this.descriptionInput = '';
            this.linkInput = '';
        }, 
        confirmError(){
            this.inputIsInvalid = false;
        }
    },
    inject: ['addResource']
}

</script>
<style scoped>
label{
    font-weight: bold;
    display: block;
    margin-bottom: 0.5rem;
}

input, 
textarea{
    display: block;
    width: 100%;
    font: inherit;

    padding: 0.15rem;
    border: 1px solid #ccc;

}

input:focus,
textarea:focus{
    outline: none;
    border-color: #3a0061;
    background-color: #f7ebff;
}

.form-control{
    margin: 1rem 0;
}
</style>