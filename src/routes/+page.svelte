<script>
	import { MaterialApp, Button } from 'svelte-materialify';
	import TaskItem from '../components/TaskItem.svelte';
	console.log('hello world');
	let taskInputValue = '';
	let tasks = [];
	$: {
		console.log('something is being updated!');
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
						<TaskItem {task} {i}/>
					{/each}
				</tbody>
			</table>
		{/if}
	</div>
</MaterialApp>
