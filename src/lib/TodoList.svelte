<script>
	import Button from './Button.svelte';
    import {createEventDispatcher} from "svelte";

	export let todos = [];
	// let input;
	let inputText = '';

    const dispatch = createEventDispatcher();

	function handleAddTodo() { 
        const isNotCanceled = dispatch('addtodo', {
            title: inputText
        }, {cancelable: true});
        if (isNotCanceled) {
            console.log("hello");
        }
    }
</script>

<div class="todo-list-wrapper">
	<ul>
		<!-- {#each todos as todo, index} -->
		{#each todos as { id, title }, index (id)}
			{@const number = index + 1}
			<li>{number} {title}</li>
			<!-- <li>{index + 1} {todo.title}</li> -->
		{/each}
	</ul>
	<form class="add-todo-form" on:submit|preventDefault={handleAddTodo}>
		<!-- <input bind:this={input}/> -->
		<!-- <input on:input={(e) => {
            inputText = e.currentTarget.value;
            // console.log(e.currentTarget.value);
        }}/> -->
		<input bind:value={inputText} />
		<Button type="submit" disabled={!inputText}>Add</Button>
	</form>
</div>
