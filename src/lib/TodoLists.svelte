<script>
  import Button from "./Button.svelte";
  import {createEventDispatcher} from "svelte"

    export let todos = []
    let inputText = "";
    const dispatch = createEventDispatcher();

    function handleAddTodo(){
        const isNotCancelled = dispatch('addtodo', {
            title: inputText
        }, {cancelable: true});
        if (isNotCancelled){
            inputText = "";
        }
    }
    
    function handleRemoveTodo(id){
        dispatch('removetodo', {id});
    }
</script>

<div class="todo-list-wrapper">
    <ul>
        {#each todos as todo}
            <li>
                <label>
                    <input type="checkbox" checked={todo.completed} />
                    {todo.title}
                </label>
                <button on:click={() => handleRemoveTodo(todo.id)}>Remove</button>
            </li>
        {/each}
    </ul>
    <form class="add-todo-form" on:submit|preventDefault={handleAddTodo}>
        <input bind:value = {inputText}/>
        <Button type="submit" disabled={!inputText}>Add</Button>
    </form>
</div>