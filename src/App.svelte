
<svelte:options immutable={true} />

<script>
    import TodoLists from './lib/TodoLists.svelte';
    import {v4 as uuid} from "uuid";

    let todos = [
        {
            id: uuid(),
            title: "Todo1",
            completed: true
        },{
            id: uuid(),
            title: "Todo2",
            completed: false
        },{
            id: uuid(),
            title: "Todo3",
            completed: true
        },
    ]

    function handleAddTodo(event){
        // event.preventDefault();
        todos.push({
            id: uuid(),
            title: event.detail.title,
            completed: false
        });
        todos = todos;
    }

    function handleRemoveTodo(event){
        todos = todos.filter(t => t.id !== event.detail.id)
    }
</script>


<TodoLists {todos} 
    on:addtodo={handleAddTodo}
    on:removetodo={handleRemoveTodo}
/>

<style>

</style>