<template>
  <div id="app">
    <TodoHeader />
    <TodoInput @addTodo="addTodo" />
    <TodoList
      :propsdata="todoItems"
      @removeTodo="removeTodo"
    />
    <TodoFooter @removeAll="clearAll" />
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';

export default {
    components: {
        TodoHeader,
        TodoInput,
        TodoList,
        TodoFooter,
    },
    data() {
        return {
            todoItems: [],
        };
    },
    created() {
        if (localStorage.length > 0) {
            // eslint-disable-next-line no-plusplus
            for (let i = 0; i < localStorage.length; i++) {
                if (localStorage.key(i) !== 'loglevel:webpack-dev-server') {
                    this.todoItems.push(localStorage.key(i));
                }
            }
        }
    },
    methods: {
        addTodo(todoItem) {
            localStorage.setItem(todoItem, todoItem);
            this.todoItems.push(todoItem);
        },
        removeTodo(todoItem, index) {
            localStorage.removeItem(todoItem);
            this.todoItems.splice(index, 1);
        },
        clearAll() {
            localStorage.clear();
            this.todoItems = [];
        },
    },
};
</script>

<style>
#app{
    text-align:center;
}
</style>
