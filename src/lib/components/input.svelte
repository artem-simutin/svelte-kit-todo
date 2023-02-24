<script lang="ts">
    export let value: string
</script>

<div class="px-3 py-2 flex justify-between rounded border outline-none border-slate-200 bg-white/10 backdrop-blur-sm">
    <input type="text" class="outline-none border-none bg-transparent w-full text-white" bind:value {...$$restProps}/>
</div>