<template>
    <FilterMenu />
    <div class="todo">
        <ToDoItem />
        <ToDoItem />
        <ToDoItem /> 
    </div>

</template>

<script>
import ToDoItem from './ToDoItem.vue';
import FilterMenu from './FilterMenu.vue';

export default {
  components: {
    ToDoItem,
    FilterMenu
  }
}
</script>

<style scoped>

    .toDoItem {
        margin-bottom: 1em;
        width: 30em;
        display: flex;
        justify-content: space-between;
    }

</style>