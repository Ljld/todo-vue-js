<template>
    
    <div class="filter-menu">
        <nav>
            <h2 @click="filter = 'all'" :class="{active: filter == 'all'}">All</h2>
            <h2 @click="filter = 'to-do'" :class="{active: filter == 'to-do'}">To Do</h2>
            <h2 @click="filter = 'done'" :class="{active: filter == 'done'}">Done</h2>
        </nav>
    </div>

    <button @click="newTodo">+</button>
    <div class="todos">
        <transition-group name="list" tag="div">
            <div class="wrapper" v-for="(todo, index) in todos" :key="todo.id">
                <ToDo
                    v-if="filter == 'all' || (filter == 'to-do' && !todo.completed) || (filter == 'done' && todo.completed)"
                    :text="todo.text"
                    :class="{completed: todo.completed}"
                    @validate="todos[index].completed = true"
                    @cancel="todos.splice(index, 1)"
                    @updatedTask="todos[index].text = $event" 
                />
            </div>
                
        </transition-group>
    </div>
</template>

<script>
import ToDo from './ToDo.vue';

export default {
  components: {
    ToDo
  },
  data () {
      return {
          increment: 3,
          filter: 'to-do',
          todos: [
              {
                id: 1,
                text: "Do the laundry",
                completed: false
              },
              {
                id: 2,
                text: "Water the plants",
                completed: true
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
        width: 100%;
    }

    .wrapper, .todos > div {
        width: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
    }

    .toDo {
        background-color: #ececec;
        border: none;
        border-radius: 50px;
        padding: 1em 2em;
        margin-bottom: 1em;
        margin-left: auto;
        margin-right: auto;
        width: 60%;
        max-width: 90%;
        display: flex;
        justify-content: space-between;
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
        margin-bottom: 1rem;
    }

    button:hover {
        border: 4px solid white;
    }


    h2 {
        border-bottom: 1px solid #2c3e50;
        margin-bottom: 1rem;
        padding: 0 1em;
        min-width: 5em;
        max-width: 5em;
    }

    .active {
        color: white;
        border-bottom: 1px solid white;
    }

    .filter-menu {
        display: flex;
        justify-content: center;
    }

    nav {
        width: 70%;
        display: flex;
        justify-content: center;
    }

    nav > div {
        flex-grow: 1;
        border-bottom: 1px solid #2c3e50;
        
        margin-bottom: 1em;
        
    }


</style>