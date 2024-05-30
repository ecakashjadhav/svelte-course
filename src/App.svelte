

<script>
    import TodoLists from './lib/TodoLists.svelte';
    import {v4 as uuid} from "uuid";

    const todos = [
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
</script>


<TodoLists {todos} />

<style>

</style>