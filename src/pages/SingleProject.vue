<script>
import axios from 'axios';
import {store} from '../store.js';
export default {
    name: 'SingleProject',
    
    data(){
      return{
        store,
        project: null
        }
    },
    created() {
        this.getSingleProject();
    },
    methods: {
        getSingleProject(){
            axios.get(`${this.store.baseUrl}/api/projects/${this.$route.params.slug}`).then((response) =>{
                if(response.data.success){
                    this.project = response.data.project;
                }
                else{
                    this.$router.push({ name: 'not-found'})
                }
            });
        }
    },
}
</script>
<template lang="">
    <div>
        <div class="container">
            <div class="row my-5">
                <div class="col-12">
                    <h1 class="text-center">{{ project.title }}</h1>
                </div>
            </div>
            <div class="row">
                <div class="col-12">
                    <p>{{ project.content }}</p>
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss" scoped>
    
</style>