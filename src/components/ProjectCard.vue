<script>
import { store } from '../store.js';

export default {
    name: 'ProjectCard',
    props: {project: Object},
    data(){
      return{
        store,
        }
    },
    methods: {
        truncateText(text){
        if(text.length > 50){
          return text.substr(0,50) + '...';
        }
        return text;
      }
    },
}
</script>
<template lang="">

    <div class="card my-3">
        <div class="card-header bg-primary text-light">
            {{ project.title }}
        </div>
        <div class="card-body">
            {{ truncateText(project.content) }}
        </div>
        <div class="card-footer">
            <router-link class="btn btn-sm btn-primary" :to="{ name: 'single-project', params: { slug: project.slug }}">Leggi il progetto</router-link>
        </div>  

    </div>
</template>
<style lang="scss" scoped>
    
</style>