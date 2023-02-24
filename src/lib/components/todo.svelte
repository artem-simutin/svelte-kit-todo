<script lang="ts">
    import type {Todo} from '$lib/types/todo.type'
	import { getContext } from 'svelte';
	import type { Writable } from 'svelte/store';

    export let todo: Todo

    const todos = getContext<Writable<Todo[]>>('todos');

    const removeTodo = () => {
        todos.update(prev => prev.filter(item => item.id !== todo.id))
    }
</script>

<div class="p-2 flex w-full items-center justify-between rounded-lg border border-slate-200 bg-white/20 backdrop-blur-lg">
    <div class="flex gap-x-2 items-center">
        <span class="text-slate-500 text-sm">#{todo.id}</span>
        <p>{todo.text}</p>
    </div>
    <div class="flex gap-x-2 items-center">
        <p class="text-slate-300"><span class="text-slate-500">by</span> {todo.author}</p>
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <p on:click={removeTodo} class="p-1 rounded bg-red-500 text-white cursor-pointer">X</p>
    </div>
</div>