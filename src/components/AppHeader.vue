<template>
    <div class="app-header d-flex">
        <h1>Todo List</h1>
        <h2>{{this.do}} more to do, {{this.done}} done</h2>
    </div>
</template>

<script>
    export default {
        name: "AppHeader",
        props: ['do', 'done']
    }
</script>

<style scoped>
    .app-header {
        align-items: flex-end
    }
    .app-header h1 {
        flex-grow: 1
    }
    .app-header h2 {
        font-size: 1.2rem;
        color: grey
    }
</style>