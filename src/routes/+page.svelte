<script lang="ts">
    import type {Todo as TodoType} from '$lib/types/todo.type'
	import { getContext, setContext } from 'svelte';
	import { writable, type Writable } from 'svelte/store';
	import Todo from '$lib/components/todo.svelte';
	import type { AuthState } from '$lib/types/auth-state.type';
	import AddTodoForm from '$lib/components/add-todo-form.svelte';

    let todos = writable<TodoType[]>([{author: 'Artem', id: 's5', text: 'Create SVELTE todo application ❤️‍🔥❤️‍🔥❤️‍🔥'}])
    setContext('todos', todos)

    const auth = getContext<Writable<AuthState>>('auth');
</script>

<div class="flex flex-col gap-y-3 items-center w-full">
    <h1 class="text-4xl font-semibold">Welcome 👋🏼</h1>
    <p class="text-slate-500">You logged in as 📧 <span>{$auth}</span></p>

    <AddTodoForm />

    <!-- Todo list -->
    <div class="flex flex-col w-full max-w-3xl gap-y-2">
        {#each $todos as todo}
            <Todo todo={todo} />
        {/each}
    </div>
</div>


