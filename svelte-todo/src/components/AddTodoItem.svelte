<script>
    import {onMount, tick} from 'svelte'
    import {getTodos} from '../utils/getTodos'
    import {format} from '../utils/format'
    export let title = 'Enter what do you want todo:'
    export let buttonTitle = 'Add todo'

    let items = []
  
    onMount(() => {
      const get = async () => {
          items = await getTodos()
      }
      get()
    })

    function handleAddClick() {
        items = [...items, 'item']
    }

    $: console.log(items)

    let text = ''
    async function handleChangeText(event) {
        const {selectionStart, selectionEnd, value} = this
        text = format(event.target.value)

        await tick()
        this.selectionStart = selectionStart
        this.selectionEnd = selectionEnd
    }

</script>

<div class='main-container'>
    <label for="todo=text">{title}</label>
    <input 
        class='todo-input'
        id="todo-text" 
        on:input={handleChangeText}
        value={text}
      />
    <button on:click={handleAddClick}>{buttonTitle}</button>
</div>
{JSON.stringify(items)}


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