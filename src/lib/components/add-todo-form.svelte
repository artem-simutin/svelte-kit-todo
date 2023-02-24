<script lang="ts">
	import Input from "$lib/components/input.svelte"
    import type {Writable} from 'svelte/store'
	import { getContext } from "svelte";
	import type { AuthState } from "../types/auth-state.type";
	import type { Todo } from "../types/todo.type";
    import {generateUID} from '$lib/utils/generate-uid'

    let text = ''

    const nickname = getContext<Writable<AuthState>>('auth')
    const todos = getContext<Writable<Todo[]>>('todos')

    const addTodo = () => {
        console.log('text', text)
        if (!$nickname || !text) return;
        const payload: Todo = {
            id: generateUID(),
            author: $nickname as string,
            text
        }
        todos.update(prev => [...prev, payload])
        text = ''
    }
</script>

<form on:submit={addTodo} class="flex flex-col items-center gap-y-3">
    <p>Add a new TODO</p>
    <Input bind:value={text} />
    <button type="submit">Add TODO</button>
</form>