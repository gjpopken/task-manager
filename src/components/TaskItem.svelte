<script>
	import { MaterialApp, Button } from 'svelte-materialify';
	import { createEventDispatcher } from 'svelte';
	export let task;
	export let i;

    const dispatch = createEventDispatcher();

    const handleDelete = () => {
        dispatch('deleteTask', {
            id: i
        })
    }
</script>

<tr>
	<td>
		{task}
	</td>
	<td>
		<Button>Mark Complete</Button>
	</td>
	<td>
		<Button class="red white-text" on:click={handleDelete}>Delete</Button>
	</td>
</tr>
