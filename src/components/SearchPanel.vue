<template>
    <div  class="top-panel d-flex">
        <input
               v-on:input="$emit('input', $event.target.value)"
               v-bind:value="searchString"
               type="text" class="form-control search-input" placeholder="type to search">

    </div>
</template>

<script>
    export default {
        name: "SearchPanel",
        props: ['searchString'],
    }
</script>

<style scoped>

    .search-input {
        width: auto;
        flex-grow: 1;
        margin-right: 3px
    }

</style>