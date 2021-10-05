<template>
    <div class="toDo">
        <input @input="$emit('updatedTask', $event.target.value, this.id)" type="text" :value="this.text"/>
        
        <div class="buttons">
            <button @click="$emit('validate')" class="complete-button">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M16 8L10.5 15.3333L8 12" stroke="#111111" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M12 22C17.5228 22 22 17.5228 22 12C22 6.47715 17.5228 2 12 2C6.47715 2 2 6.47715 2 12C2 17.5228 6.47715 22 12 22Z" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
            </button>
            <button @click="$emit('cancel')" class="cancel-button">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M12 22C17.5228 22 22 17.5228 22 12C22 6.47715 17.5228 2 12 2C6.47715 2 2 6.47715 2 12C2 17.5228 6.47715 22 12 22Z"  stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M15 9L9 15" stroke="#111111" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M9 9L15 15" stroke="#111111" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
            </button>
        </div>
    </div>
</template>

<script>

export default {
    props: {
        id: Number,
        text: String,
        completed: Boolean
    },
    emits: ['validate', 'cancel', 'updatedTask']
}
</script>

<style scoped>

    input {
        background-color: transparent;
        outline: none;
        width: 70%;
        border: none;
        border-bottom: 1px solid #ececec;
        padding: 0em 1em;
        transition: 200ms border-bottom linear;
    }

    input:focus {
        border: none;
        outline: none;
        border-bottom: 1px solid rgba(0, 0, 0, 0.3);
    }

    svg {
        width: 2.5em;
        height: 2.5em;
    }

    svg > path {
        fill: transparent;
        stroke: #d0d0d0;
    }

    button {
        width: 4em;
        height: 4em;
        border: none;
        background-color: transparent;
        transition: 150ms all linear;
    }

    button:hover {
        filter: brightness(50%);
    }

    button:active {
        filter: brightness(100%);
    }

    .cancel-button:active > svg > path  {
        stroke: red;
    }

    .complete-button:active > svg > path {
        stroke: green;
    }

    .completed > .buttons > .complete-button > svg > path {
        stroke: green;
    }

</style>