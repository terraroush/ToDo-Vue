<template>
  <div>
      <h3 :class="{completed: todo.complete}">{{todo.name}}</h3>
      <button @click="handleClick">Mark Complete</button>
</div>
</template>

<script>
export default {
    props: ["todo"],

    methods: {
        handleClick() {
            this.$emit("status-change", this.todo);
        }
    }
}
</script>

<style scoped>
div {
    align-self: center;
    border: 1px solid black;
    margin: 10px;
    padding: 10px;
    width: 400px;
}
button {
    align-self: center;
    width: 175px;
    padding: 8px;
}
.completed {
    text-decoration: line-through;
    text-decoration-color: navy;
}

</style>