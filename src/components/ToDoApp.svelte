<script>
	import { onMount } from "svelte";
    import ToDoControls from "./ToDoControls.svelte";
    import ToDoItem from "./ToDoItem.svelte";

    let items = [];
    let id=0;

    onMount(()=>{
        if(localStorage.key("items")){
            items = JSON.parse(localStorage.getItem("items"));
        }
        if(items.length){
        items.forEach((i)=>{
            if (id<i.id){
                id=i.id;
            }
        });
        id++;
    }
    });

    function onChangeStatus(event) {
        const item= items.find((i)=>i.id===event.detail.id);
        item.isDone= !item.isDone;
        items = items;
        localStorage.setItem("items", JSON.stringify(items));
    }

    function onAddItem(event) {
        const item = {
            id: id++,
            text: event.detail.text,
            isDone: false
        };
        items.push(item);
        items=items;
        localStorage.setItem("items", JSON.stringify(items));
    }
    function del(event){
        const idx = items.findIndex(i=>i.id===event.detail.id);
        items.splice(idx, 1);
        items=items;
        localStorage.setItem("items", JSON.stringify(items));
    }
</script>

<div class="todo-app">
    <ToDoControls on:добавить={onAddItem}/>
    <div class="todo-app_1">
        {#each items as item}
          <!-- svelte-ignore missing-declaration -->
          <ToDoItem id={item.id} text={item.text} isDone={item.isDone} on:change={onChangeStatus} on:del={del}/>  
        {/each}
    
    </div>
</div>

<style>
    .todo-app{
        width: 700px;
        height: 80%;
        background: rgb(231, 133, 203);
        border-radius: 15px;
        padding: 30px;
        display:flex;
        flex-direction: column;
        gap: 30px;
    }
    .todo-app_1{
        background: rgb(255, 255, 255)(255, 255, 255);
        flex-grow: 1;
        border-radius: 15px;
        overflow-y: auto;
        padding:20px;
        display: flex;
        flex-direction: column;
        gap: 12px;
    }

</style>
    

<!--
<script>
	import { onMount } from "svelte";
	import ToDoControls from "./ToDoControls.svelte";
	import ToDoItem from "./ToDoItem.svelte";

    let items=[];
    let id = 0;


    onMount(()=>{
        if (localStorage.key('items')) {
            items = JSON.parse(localStorage.getItem("items"));
        }
        if (items.lenght){
        items.forEach((i)=>{
            if(id < i.id) {
                id = i.id;
            }
        });
        id++;
        }
    });

    function onChangeStatus(event) {
        const item = items.find((i) => i.id === event.detail.id);
        item.isDone = !item.isDone;
        items=items;
        localStorage.setItem('items', JSON.stringify(items));
    }

    function onAddItem(event) {
        console.log(event)
        const item={
            id: id++,
            text: event.detail.text,
            isDone: false
        };
        items.push(item);
        items = items;
    }
    function onDeleteItem(event) {
        const idx = items.findIndex((i)=>i.id === event.detail.id);
        items.splice(idx, 1);
        items = items;
    }
</script>


<div class="todo-app">
    <ToDoControls on:add={onAddItem}/>
    <div class="todo-app_field">
        {#each items as item}
        <ToDoItem 
        id={item.id} 
        text={item.text} 
        isDone={item.isDone} 
        on:change={onChangeStatus} 
        on:remove={onDeleteItem}/>
        {/each}
    </div>
</div>


<style>
    .todo-app {
        width: 700px;
        height: 80%;
        background: rgb(0, 0, 0);
        border-radius: 15px;
        padding: 40px;
        display: flex;
        flex-direction: column;
        gap: 30px;
    }
    .todo-app_field {
        background: white;
        flex-grow: 1;
        border-radius: 15px;
        overflow-y: auto;
        padding: 20px;
        display: flex;
        flex-direction: column;
        gap: 20px;
    }
</style>
-->