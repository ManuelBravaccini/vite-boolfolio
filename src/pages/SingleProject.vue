<script>
import ProjectCard from '../components/partials/ProjectCard.vue';
import axios from 'axios';

export default {
    name: 'SingleProject',

    components: {
        ProjectCard
    },

    data() {
        return {
            project: null,
            loading: false,
            apiUrl: 'http://127.0.0.1:8000',
        }
    },

    methods: {
        getProjects() {
            axios.get(this.apiUrl + '/api/projects/', {
                params: {
                }
            })
                .then((response) => {
                    this.projects = response.data.results.data;
                })
                .catch(function (error) {
                    console.log(error);
                })
                .finally(function () {
                    // always executed
                });
        }
    },

    created() {
        this.getProjects();
    },
}
</script>

<template>
    <div class="row">
        <ProjectCard :project="project" v-for="(project, index) in projects" :key="index" />
    </div>
</template>

<style lang="">
    
</style>