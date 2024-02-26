<script>
	import { MaterialApp, Button } from 'svelte-materialify';
	import TaskItem from '../components/TaskItem.svelte';
	console.log('hello world');
	let taskInputValue = '';
	let tasks = [];
	$: {
		console.log('something is being updated!');
	}

    const runDelete = (id) => {
        console.log("Deleting this index: ", id);
        console.log("What is getting deleted:", tasks.toSpliced(id, 1));
        tasks = tasks.toSpliced(id, 1)
    }
</script>

<MaterialApp>
	<h3>Welcome to Svelte Tasks Manager!</h3>

	<label for="taskInput"
		>New Task:
		<input type="text" id="taskInput" bind:value={taskInputValue} />
	</label>
	<Button
		on:click={() => {
			console.log('click');
			tasks = [...tasks, taskInputValue];
			taskInputValue = '';
		}}>Add Task!</Button
	>

	<div>
		{#if tasks.length === 0}
			<p>There are no tasks!</p>
		{:else}
			<table>
				<thead>
					<tr>
						<td>Task:</td>
						<td>Complete?</td>
						<td>Delete?</td>
					</tr>
				</thead>
				<tbody>
					{#each tasks as task, i}
						<TaskItem {task} {i} on:deleteTask={(event) => runDelete(event.detail.id)}/>
					{/each}
				</tbody>
			</table>
		{/if}
	</div>
</MaterialApp>
