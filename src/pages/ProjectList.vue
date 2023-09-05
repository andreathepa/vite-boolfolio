<script>
import axios from 'axios';
import {store} from '../store.js'

export default {
    name: 'ProjectList',
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
      truncateText(text){
        if(text.length > 50){
          return text.substr(0,50) + '...';
        }
        return text;
      }
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
        <div class="card my-3">
          <div class="card-header bg-primary text-light">
            {{ project.title }}
          </div>
          <div class="card-body">
            {{ truncateText(project.content) }}
          </div>  

        </div>
      </div>

    </div>
  </div>
</template>

<style lang='scss' scoped>


</style>