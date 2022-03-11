<script lang="ts">
    import { createEventDispatcher } from 'svelte';

    export let key: string;
    export let value: string;

    const dispatch = createEventDispatcher();

    const remove = () => {
        dispatch('remove', key);
    };
</script>

<div class="flex items-stretch my-2 border rounded bg-slate-800 text-teal-300">
    <div class="w-5/12 p-2 border-r border-white">
        {key}
    </div>
    <div class="w-5/12 p-2 border-r border-white">
        {value}
    </div>
    <button class="btn w-2/12 p-2 text-red-500 hover:bg-slate-900" on:click={remove}>&times;</button
    >
</div>
