<script lang="ts">
	import { getContext, setContext } from "svelte";
	import { writable, type Writable } from "svelte/store";
    import type {AuthState} from '$lib/types/auth-state.type'
    import "./styles.css"
	import Form from "$lib/components/login-form.svelte";

    setContext('auth', writable<AuthState>(null))

    const isAuthenticated = getContext<Writable<AuthState>>('auth')
</script>


<svelte:head>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link href="https://fonts.googleapis.com/css2?family=Shantell+Sans:wght@400;600&display=swap" rel="stylesheet" />
</svelte:head>


<div class="flex flex-col w-full  items-center">
    {#if !$isAuthenticated}
        <Form />
        {:else}
        <slot />
    {/if}
</div>