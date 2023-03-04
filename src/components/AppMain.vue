<script>
import axios from 'axios';
import ProjectCard from './partials/ProjectCard.vue';

export default {
    name: 'AppMain',

    components: {
        ProjectCard,
    },

    data() {
        return {
            projects: [],
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
    <section>
        <div class="container">
            <div class="row mb-5">
                <h1>Projects:</h1>
            </div>
            <div class="d-flex flex-wrap gap-5">
                <ProjectCard :project="project" v-for="(project, index) in projects" :key="index" />
            </div>
        </div>
    </section>
</template>

<style lang="">
    
</style>