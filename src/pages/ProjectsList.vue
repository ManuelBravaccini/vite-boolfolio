<script>
import axios from 'axios';
import ProjectCard from '../components/partials/ProjectCard.vue';

export default {
    name: 'ProjectsList',

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

<template lang="">
    <div class="container">
        <div class="row">
            <!-- TODO loader -->
            <div class="col-12 mb-3">
                <h2>
                    Projects:
                </h2>
            </div>
        </div>
        <div class="row justify-content-around">
            <ProjectCard :project="project" v-for="(project, index) in projects" :key="index" />
        </div>
    </div>
</template>

<style lang="">
    
</style>