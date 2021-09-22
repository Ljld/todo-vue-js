<template>
    <div class="filter-menu">
        <nav>
            <h2 class="active">To Do</h2>
            <h2>Done</h2>
        </nav>
    </div>
</template>

<script>

export default {
  name: 'FilterMenu'
}
</script>

<style scoped>

    .filter-menu {
        width: 15em;
        margin: auto;
    }

    h2 {
        border-bottom: 1px solid #2c3e50;
        padding: 0 1em;
        margin-bottom: 1em;
    }

    .active {
        color: white;
        border-bottom: 1px solid white;
    }

    nav {
        display: flex;
        justify-content: center;
    }

</style>
