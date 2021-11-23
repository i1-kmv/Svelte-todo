<script>
    export let title = 'Enter what do you want todo:'
    export let buttonTitle = 'Add todo'

    let items = []

    function handleAddClick() {
        items = [...items, 'item']
    }

    $: items
</script>



<div class='main-container'>
    <label for="todo=text">{title}</label>
    <input class='todo-input' id="todo-text">
    <button on:click={handleAddClick}>{buttonTitle}</button>
</div>


<style>
    .main-container {
        background-color: lightseagreen;
        border-radius: 5px;
        padding: 10px;
    }
    .todo-input {
        width: 100%;
    }
</style>