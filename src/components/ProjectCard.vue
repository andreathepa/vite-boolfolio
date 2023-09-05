<script>
import { store } from '../store';


    export default {
        name:"ProjectsCard",

        props:{
            project: Object
        },

        data() {
            return {
                maxNumChar:50,
                store,
                
            }
        },

        methods: {
            truncateText(text){
                    if(text.length > this.maxNumChar){
                        return text.substr(0,50) + '...'
                    }
                    return text;
                }
            
        },




        
    }

</script>


<template lang="">
     
            <div class="card my-3">
                <div class="card-header">
                    {{project.title}}
                </div>
                <div class="card-body">
                    {{truncateText(project.content)}}
                </div>
                <div class="card-footer">
                    <!-- <a href="" class="btn btn-sm btn-primary"> Guarda il progetto</a> -->
                    <router-link class="btn btn-sm btn-primary" :to="{name:'SingleProject', params:{slug:project.slug}}">Guarda il progetto</router-link>
                </div>
            </div>
       
       
</template>



<style lang="">
    
</style>