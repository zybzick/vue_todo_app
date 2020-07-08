<template>
    <div class="todo-app">
        <AppHeader :do="doItems" :done="doneItems"/>
        <div class="top-panel d-flex">
            <SearchPanel v-model="searchString"/>
            <ItemStatusFilter :visibility="visibility" @filterData="changeVisibility" />
        </div>
        <TodoListItem @onDelete="onDelete" :todoData="filteredTodoData"/>
        <ItemAddForm @onAddItem="onAddItem"/>
    </div>
</template>

<script>
    import TodoListItem from './components/TodoListItem'
    import ItemAddForm from './components/ItemAddForm'
    import AppHeader from "./components/AppHeader";
    import SearchPanel from "./components/SearchPanel";
    import ItemStatusFilter from "./components/ItemStatusFilter";

    export default {
        name: 'App',
        components: {TodoListItem, ItemAddForm, AppHeader, SearchPanel, ItemStatusFilter},
        data: () => {
            return {
                maxId: 101,
                todoData: [],
                visibility: "all",
                searchString: ''
            }
        },

        computed: {
            doItems: function () {
                return this.todoData.filter((el) => el.done !== true).length
            },
            doneItems: function () {
                return this.todoData.length - this.doItems
            },
            filteredTodoData: function () {
                const str = this.searchString
                switch (this.visibility) {
                    case 'all':
                        return this.todoData.filter((el) => el.label.toUpperCase().includes(str.toUpperCase()))
                    case 'active':
                        return this.todoData.filter((el) => {
                            return el.done === false && el.label.toUpperCase().includes(str.toUpperCase())
                        })
                    case 'done':
                        return this.todoData.filter((el) => {
                            return el.done === true  && el.label.toUpperCase().includes(str.toUpperCase())
                        })
                    default:
                        return this.todoData.filter((el) => {
                            return el.label.toUpperCase().includes(str.toUpperCase())
                        });
                }
            },
        },
        mounted() {
            this.todoData = [
                this.createTodoItem('Do 1'),
                this.createTodoItem('Do 2', true),
                this.createTodoItem('Do 3', false, true),
            ]
        },
        methods: {
            createTodoItem(label, important = false, done = false) {
                return {
                    label: label,
                    important: important,
                    done: done,
                    id: this.maxId++
                }
            },
            onDelete(id) {
                this.todoData = this.todoData.filter((el) => el.id !== id)
            },
            onAddItem(label) {
                this.todoData.push(this.createTodoItem(label))
            },
            changeVisibility(filter) {
                this.visibility = filter
            },
        },
    }
</script>

<style>
    .todo-app {
        margin: 2rem auto 0;
        max-width: 400px
    }
    .top-panel {
        margin: 1rem 0
    }
</style>
