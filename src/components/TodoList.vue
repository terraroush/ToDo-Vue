<template>
  <div>
      <h1>ToDo List</h1>
      <p>{{itemsRemaining}}</p>
      <div v-for="item in todos" :key="item.id">
          <todo-item :todo="item" @status-change="handleStatusChange"/>
      </div>
  </div>
</template>

<script>
import {todoItems} from "../data";
import TodoItem from "./TodoItem.vue";

export default {
    components: {TodoItem},
    data() {
        return {
            todos: [...todoItems],
        }
    },
    methods: {
        handleStatusChange(item) {
            item.complete = !item.complete;
            console.log(item);
        },
        remainingText(number) {
            if (number === 1) {
                return "There is 1 item left today"
            } else {
                return `There are ${number} items left today`
            }
        }
    },
    computed: {
        itemsRemaining() {
            const remaining = this.todos.filter((t) => !t.complete).length
            return this.remainingText(remaining)
        }
    }
}
</script>

<style scoped>
    div {
        display: flex;
        flex-direction: column;
        text-align: center;
    }

</style>