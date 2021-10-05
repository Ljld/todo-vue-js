<template>
    <FilterMenu />
    <button @click="newTodo">+</button>
    <div class="todos">
        <transition-group name="list" tag="div">
                <ToDo 
                    v-for="(todo, index) in todos"
                    :key="todo.id"
                    :text="todo.text"
                    :class="{completed: todo.completed}"
                    @validate="todos[index].completed = true"
                    @cancel="todos.splice(index, 1)"
                    @updatedTask="todos[index].text = $event" 
                />
        </transition-group>
    </div>
</template>

<script>
import ToDo from './ToDo.vue';
import FilterMenu from './FilterMenu.vue';

export default {
  components: {
    ToDo,
    FilterMenu
  },
  data () {
      return {
          increment: 3,
          todos: [
              {
                id: 1,
                text: "Do the laundry",
                completed: false
              },
              {
                id: 2,
                text: "Water the plants",
                completed: false
              },
              {
                id: 3,
                text: "Take over the world",
                completed: false
              }
          ]
      }
  },
  methods: {
      newTodo () {
          this.todos.push({id: this.increment + 1,text: " ", completed: false});
          this.increment++;
      }
  }
}
</script>

<style scoped>

    .todos {
        display: flex;
        justify-content: center;
    }

    .toDo {
        background-color: #ececec;
        border: none;
        border-radius: 50px;
        padding: 1em 2em;
        margin-bottom: 1em;
        width: 30em;
        display: flex;
        justify-content: center;
    }

    .completed {
        text-decoration: line-through;
    }

    .list-enter-active, .list-leave-active {
        transition: opacity .5s;
    }

    .list-enter-from, .list-leave-to {
        opacity: 0;
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