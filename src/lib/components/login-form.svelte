<script lang="ts">
	import Input from "$lib/components/input.svelte";
	import { getContext } from "svelte";
	import type { Writable } from "svelte/store";
	import type { AuthState } from "../types/auth-state.type";

    let nickname: string = ''

    const authStore = getContext<Writable<AuthState>>('auth')

    const onSubmit = () => authStore.set(nickname)
</script>

<form on:submit={onSubmit} class="flex items-center flex-col gap-y-4">
    <h1>You aren't logged in</h1>
    <Input placeholder="Nickname" bind:value={nickname} />
    <button type="submit">Continue</button>
</form>