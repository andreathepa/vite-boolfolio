<script>
import axios from 'axios';
import {store} from '../store.js';
import ProjectCard from '../components/ProjectCard.vue'

export default {
    name: 'ProjectList',

    components:{
      ProjectCard
    },

    data(){
      return{
        store,
        projects: [],
        }
    },
    created(){
      this.getProjects();
    },
    methods:{
      getProjects(){


        axios.get(`${this.store.baseUrl}/api/projects`).then(( response) => {
          if(response.data.success){
            this.projects = response.data.results;

            

          }
          else{

          }

        })

      },
    }
  }
</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1 class="text-center my-5">Progetti</h1>
      </div>
    </div>
  </div>
  
  <div class="container">
    <div class="row">
      <div class="col-12 col-md-4" v-for="project in projects" :key="project.id">
        <ProjectCard :project="project" />
      </div>

    </div>
  </div>
</template>

<style lang='scss' scoped>


</style>