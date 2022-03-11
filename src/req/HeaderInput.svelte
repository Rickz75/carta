<script lang="ts">
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    let key = '';
    let value = '';

    const submit = () => {
        dispatch('submit', { key, value });
        key = '';
        value = '';
    };
</script>

<div class="flex items-stretch my-2 border rounded border-gray-400">
    <input
        class="w-5/12 p-2 outline-none border-r border-gray-400"
        type="text"
        placeholder="key"
        bind:value={key}
    />
    <input
        class="w-5/12 p-2 outline-none border-r border-gray-400"
        type="text"
        placeholder="value"
        bind:value
    />
    <button class="btn w-2/12 p-2 bg-slate-800 text-teal-300 hover:bg-slate-900" on:click={submit}>
        SET
    </button>
</div>
