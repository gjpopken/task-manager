<script>
	import { MaterialApp, Button } from 'svelte-materialify';
	export let task;
    export let i;
</script>

	<tr>
		<td>
			{task}
		</td>
		<td>
			<Button>Mark Complete</Button>
		</td>
		<td>
			<Button class="red white-text" on:click>Delete</Button>
		</td>
	</tr>
