<template>
    <header>
        <h1>{{title}}</h1>
        <Button text="Add Task" color="green"  data-toggle="collapse" data-target="#collapseExample" aria-expanded="false" aria-controls="collapseExample" />
        
    </header>
</template>

<script>

import Button from "./button.vue";

export default {
    name: 'Header',
    props: ['title'],

    components: {
        Button
    }
}
</script>

<style scoped>

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}

</style>