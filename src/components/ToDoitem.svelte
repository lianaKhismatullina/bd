<script>
    export let text;
    export let id;
    export let isDone;
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();
</script>

<div class="menu" class:menu_done={isDone}>
    <input 
    class="check"
    type="checkbox"
    on:change={dispatch("change", {id})}
    checked={isDone}
    />
    <span class="text">{text}</span>
    <button class="del" on:click={dispatch("del", {id})} >Удалить</button>
</div>

<style>
    .menu{
        display: flex;
        align-items:center;
        justify-content: space-between;
        padding: 15px;
        background: rgb(104, 242, 177);
        border-radius: 15px;

    }
    .menu_done{
        background: rgb(196, 179, 244);
    }
    .menu_done .text{
        text-decoration: line-through;
    }
    .del{
        border:none;
        border-radius:10px;
        background: rgb(146, 37, 37);
        padding: 10px;
        min-width: 150px;

    }
    .text{
        flex-grow:1;
    }

</style>


<!--
<script>
    export let id;
    export let text;
    export let isDone;
    import { createEventDispatcher } from "svelte";


    const dispatch = createEventDispatcher();
</script>

<div class="todo-item" class:todo-item_done={isDone}>
    <input
     class="todo-item_check" 
     type="checkbox" 
     on:change={dispatch("change", {id})} 
     checked={isDone}
    />
    <span class="todo-item_text">{text}</span>
    <button class="todo-item_btn" on:click={dispatch("remove", {id})}>Удалить</button>
</div>


<style>
    .todo-item{
        display:flex;
        align-items: center;
        justify-content: space-between;
        padding: 15PX;
        background: rgb(144, 110, 255);
        border-radius: 10px;
    }
    .todo-item_done {
        background: rgb(94, 13, 0);
        text-decoration: line-through;
    }
    .todo-item_done .todo-item_text {
        text-decoration: line-through;
    }
    .todo-item_check {
        width: 20px;
        font-size:20px;
    }
    .todo-item_text {
        flex-grow: 1;
    }
    .todo-item_btn{
        border: none;
        border-radius: 10px;
        background-color: rgb(255, 245, 172);
        padding: 10px;
        min-width: 100px;


    }
</style>
-->
