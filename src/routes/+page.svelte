<script>
	console.log('hello world');
    let taskInputValue = ''
    let tasks = [];
    $: {
        console.log('something is being updated!');
        }
</script>

<h1>Welcome to Svelte Tasks Manager!</h1>

<label for="taskInput"
	>New Task:
	<input type="text" id="taskInput" bind:value={taskInputValue}/>
</label>
<button on:click={() => {console.log('click');tasks = [...tasks, taskInputValue];taskInputValue=''}}>Add Task!</button>

<div>
	{#if tasks.length === 0}
		<p>There are no tasks!</p>
	{:else}
		{#each tasks as task}
			<p>{task}</p>
		{/each}
	{/if}
</div>
