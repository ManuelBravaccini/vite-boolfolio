<script>
export default {
    name: 'ProjectCard',

    props: {
        project: {
            type: Object,
            required: true
        }
    },

    data() {
        return {
        }
    },

    methods: {
    },

    created() {
    },
}
</script>

<template>
    <article class="card col-2">

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
</template>

<style lang="">
    
</style>