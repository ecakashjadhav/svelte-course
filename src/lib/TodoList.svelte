<script>
	import Button from './Button.svelte';
	import { v4 as uuid } from 'uuid';

	export let todos = [];
	// let input;
	let inputText = '';

	function handleAddTodo() {
		// 1st way
		// if (!inputText) return;
		// todos.push({
		//     title:inputText,
		//     id:uuid(),
		//     completed:false
		// });
		// todos = todos;

		//2nd way
		todos = [
			...todos,
			{
				title: inputText,
				id: uuid(),
				completed: false
			}
		];
        inputText = '';
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
