<script>
import axios from 'axios';
export default {
    name: 'AppMain',
    data(){
      return{
        baseUrl:'http://localhost:8000',
        projects: [],
        maxNumCharacters: 200,
        currentPage:1,
        lastPage:null,
        }
    },
    created(){
      this.getProjects(1);
    },
    methods:{
      getProjects(num_page){


        axios.get(`${this.baseUrl}/api/projects`, { params: {page: num_page}}).then(( response) => {
          if(response.data.success){
            this.projects = response.data.results.data;
            this.currentPage = response.data.results.current_page;
            this.lastPage = response.data.results.last_page;

          }

        });

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
          <div class="card-header">
            {{ project.title }}
          </div>
          <!-- <div class="card-image-top">
            <img :src="${baseUrl}/storage/${project.image}" alt="img">
          </div> -->
          <div class="card-body">
            <div>
              <span v-if="project.category">{{ project.category.name }}</span>
              <span v-else>Categoria non assegnata</span>
            </div>
            <div v-if="project.technologies">
              <span class="badge text-bg-primary me-3" v-for="technology in project.technologies" :key="technology.id">
                {{ technology.name }}
              </span>
            </div>
            <div>
              {{ truncateText(project.content) }}
            </div>
          </div>
          <div>
            <a href="#" class="btn btn-sm btn-primary">Leggi il progetto</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang='scss' scoped>


</style>