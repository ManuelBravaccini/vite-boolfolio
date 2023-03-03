<script>
import axios from 'axios';

export default {
    name: 'AppMain',
    data() {
        return {
            projects: [],
            loading: false,
            urlAddress: 'http://127.0.0.1:8000/api/projects',
        }
    },

    methods: {
        getProjects() {
            axios.get(this.urlAddress, {
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
                <article class="card col-2" v-for="(project, index) in projects" :key="index">
                    <img :src=project.image class="card-img-top" :alt=project.image>
                    <div class="card-body">
                        <h5 class="card-title">
                            {{ project.title }}
                        </h5>
                        <p class="card-text">
                            {{ project.content.substr(0, 50) }}...
                        </p>
                        <a href="#" class="btn btn-primary">Show project</a>
                    </div>
                </article>

            </div>
        </div>
    </section>
</template>

<style lang="">
    
</style>