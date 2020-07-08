<template>
    <div class="item-status-filter">
        <div class="btn-group" v-for="button in buttons" :key="button.name">
            <button type="button"
                    class="btn"
                    @click="$emit('filterData', button.name)"
                    :class="[ visibility===button.name ? 'btn-info' : 'btn-outline-secondary']"
            >{{button.label}}</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "ItemStatusFilter",
        props: ['visibility'],
        data: ()=> {
            return {
                buttons: [
                    {name: 'all', label: 'All'},
                    {name: 'active', label: 'Active'},
                    {name: 'done', label: 'Done'}
                ],
            }
        },
    }
</script>

<style scoped>
    .item-status-filter{
        display: flex!important;
        margin: 1rem 0;
    }
</style>