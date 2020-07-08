<template>
    <ul class="list-group todo-list">
        <li class="list-group-item" v-for="item in todoData" :key="item.id">

            <span class="todo-list-item ">
                <span @click="item.done=!item.done"
                      :class="{done: item.done, important: item.important}"
                      class="todo-list-item-label">{{ item.label }}
                </span>
                <button type="button"
                        @click="item.important=!item.important"
                        class="btn btn-outline-success btn-sm float-right">
                    <i class="fa fa-exclamation"></i>
                </button>
                <button type="button"
                        @click="$emit('onDelete', item.id)"
                        class="btn btn-outline-danger btn-sm float-right">
                    <i class="fa fa-trash-o"></i>
                </button>
            </span>

        </li>
    </ul>
</template>

<script>
    export default {
        name: "TodoListItem",
        props: ['todoData'],
    }
</script>

<style scoped>
    .done {
        text-decoration: line-through
    }
    .important {
        font-weight: 700;
        color: #4682b4
    }
    .todo-list-item-label {
        margin-left: 1.25rem;
        line-height: 35px;
        cursor: pointer;
        -webkit-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none
    }
    .todo-list-item {
        font-size: 1.25rem
    }
    .todo-list-item button {
        width: 35px;
        margin: 3px
    }
    .todo-list .list-group-item {
        padding: .25rem .75rem
    }

</style>