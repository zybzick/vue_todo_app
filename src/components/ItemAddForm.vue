<template>
    <form class="item-add-form d-flex"
          v-on:submit.prevent="$emit('onAddItem', label); label=''"
    >
        <input placeholder="add item"
               class="form-control mr-2"
               type="text"
               v-model="label">
        <button type="submit"
                class="btn btn-outline-secondary">AddItem</button>
    </form>
</template>

<script>
    export default {
        name: "ItemAddForm",
        data: ()=> {
            return {
                label: ''
            }
        }
    }
</script>

<style scoped>
    .item-add-form {
        margin: 1rem 0
    }
</style>