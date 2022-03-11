<script lang="ts">
    import Status from './res/Status.svelte';
    import Header from './res/Header.svelte';
    import Body from './res/Body.svelte';
    import { createEventDispatcher } from 'svelte';

    export let promise: Promise<Response> = null;

    const dispatch = createEventDispatcher();

    const reset = () => {
        dispatch('reset');
    };
</script>

{#if promise}
    {#await promise then response}
        <h2 class="text-2xl font-normal leading-normal my-4 text-slate-800">Response</h2>
        <Status code={response.status} />
        {#each [...response.headers] as [key, value]}
            <Header {key} {value} />
        {/each}
        {#await response.text() then body}
            <Body value={body} />
        {/await}
        <button
            class="border rounded border-gray-400 p-2 w-full hover:bg-slate-800 hover:text-red-400"
            on:click={reset}>RESET</button
        >
    {:catch error}
        <div class="text-red-600 p-2 my-2">{error.message}</div>
        <button
            class="border rounded border-gray-400 p-2 w-full hover:bg-slate-800 hover:text-red-400"
            on:click={reset}>RESET</button
        >
    {/await}
{/if}
