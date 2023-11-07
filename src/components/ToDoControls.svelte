<script>
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();
    let who="";
    function click(){
        if (who.length) {
            dispatch('добавить', {text: who});
            who="";
        }
    }
</script>

<div class="todo-controls">
    <input class="vod" type="text" bind:value={who}/>
    <button class="gal" on:click={click}>Добавить</button>
</div>
<style>
    .todo-controls{
        display: grid;
        grid-template-columns: 80%20%;
    }
    .gal{
        background: rgb(9, 189, 39);
        border-radius: 0 10px 10px 0;
        border:none;

    }
    .vod{
        border: none;
        border-radius: 10px 0 0 10px;
        padding: 10px;
    }
</style>


<!--
<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    let inputValue = "";
    function onClick() {
        if(inputValue.length) {
            dispatch("add", {text: inputValue});
            inputValue="";
        }
    }
</script> 

<div class="todo-controls">
    <input class="todo-controls_input" type="text" bind:value={inputValue} />
    <button class="todo-controls_btn" on:click={onClick}>Добавить</button>
</div>

<style>
    .todo-controls {
        display: grid;
        grid-template-columns:70% 30%;
    }
    .todo-controls_input {
        border: none;
        border-radius: 10px 0 0 10px;
        padding: 15px;
    }
    .todo-controls_btn {
        border: none;
        border-radius: 0 10px 10px 0;
        background: rgb(52, 116, 236);
    }
</style>
-->
