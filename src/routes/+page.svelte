<script lang="ts">
	type Todo = {
		id: number;
		title: string;
		status: string;
	};
	let value = '';
	let count = 1;
	let array: Todo[] = [];

	function pushValue() {
		if (!value.match(/\S/g)) {
			alert('テキストを入力してください！');
		} else {
			array.push({ id: count, title: value, status: '' });
			array = array;
			value = '';
			count += 1;
			console.log(array);
		}
	}
</script>

<svelte:head>
	<title>svelte todo app</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<div>
	<div class="form-control">
		<div class="input-group">
			<input
				type="text"
				placeholder="タイトル"
				class="input input-bordered w-96 font-bold"
				bind:value
			/>
			<button class="btn btn-square w-20" on:click={pushValue}> 追加 </button>
		</div>
	</div>
	<div class="overflow-x-auto mt-10">
		<table class="table w-full">
			<thead>
				<tr>
					<td />
					<th>タイトル</th>
					<th>ステータス</th>
				</tr>
			</thead>
			<tbody>
				{#each array as todo}
					<tr>
						<th>{todo.id}</th>
						<td>{todo.title}</td>
						<td>
							<button
								class="btn btn-active bg-white border-0 shadow-xl w-14 hover:bg-white focus:bg-slate-700"
								on:click={() => (todo.status = '😎')}>😎</button
							>
							<button
								class="btn btn-active bg-white border-0 shadow-xl w-14 hover:bg-white focus:bg-slate-700"
								on:click={() => (todo.status = '😇')}>😇</button
							>
							<button
								class="btn btn-active bg-white border-0 shadow-xl w-14 hover:bg-white focus:bg-slate-700"
								on:click={() => (todo.status = '😅')}>😅</button
							>
							<button
								class="btn btn-active bg-white border-0 shadow-xl w-14 hover:bg-white focus:bg-slate-700"
								on:click={() => (todo.status = '😡')}>😡</button
							></td
						>
					</tr>
				{/each}
			</tbody>
		</table>
	</div>
</div>
