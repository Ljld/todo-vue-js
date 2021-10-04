<template>
    <FilterMenu />
    <button @click="newItem">+</button>
    <div class="todo" v-for="item in items" v-bind:key="item.id">
        <ToDoItem @cancel="deleteItem" v-bind="item" />
    </div>

</template>

<script>
import ToDoItem from './ToDoItem.vue';
import FilterMenu from './FilterMenu.vue';

export default {
  components: {
    ToDoItem,
    FilterMenu
  },
  data () {
      return {
          increment: 2,
          items: [
              {
                id: 0,
                text: "test",
                completed: false
              },
              {
                id: 1,
                text: "test 1",
                completed: false
              },
              {
                id: 2,
                text: "test 2",
                completed: false
              }
          ]
      }
  },
  methods: {
      newItem: function () {
          this.items.push({id: this.increment + 1,text: " ", completed: false});
          this.increment++;
      },
      deleteItem: function (event) {
          let index = this.items.findIndex(todo => todo.id == event);
          this.items.splice(index, 1);
      }

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

    button {
        width: 4em;
        height: 4em;
        color: white;
        border: 2px solid white;
        border-radius: 50%;
        background-color: transparent;
        transition: 150ms all linear;

        margin-bottom: 1em;
    }

    button:hover {
        border: 4px solid white;
    }

</style>