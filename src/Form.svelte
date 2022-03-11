<script lang="ts">
    import Url from './req/Url.svelte';
    import Method from './req/Method.svelte';
    import HeaderInput from './req/HeaderInput.svelte';
    import Header from './req/Header.svelte';
    import Body from './req/Body.svelte';

    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    let url = '';
    let method = 'GET';
    let headers = new Headers();
    let rawBody = '';

    const setHeader = (key: string, value: string) => {
        if (key.length > 0 && value.length > 0) {
            headers.set(key, value);
            headers = headers;
        }
    };

    const removeHeader = (key: string) => {
        headers.delete(key);
        headers = headers;
    };

    const submit = () => {
        let body = null;

        if (rawBody.length > 0) {
            body = rawBody;
        }

        dispatch(
            'submit',
            new Request(url, {
                method,
                headers,
                body,
            })
        );
    };
</script>

<main class="container mx-auto">
    <h2 class="text-2xl font-normal leading-normal mt-0 my-4 text-slate-800">Request</h2>
    <div class="flex items-flex my-4 border rounded border-gray-400">
        <Url bind:value={url} />
        <Method bind:value={method} />
    </div>
    <h3 class="text-1xl font-normal leading-normal my-4 text-slate-800">Headers</h3>
    <HeaderInput on:submit={(e) => setHeader(e.detail.key, e.detail.value)} />
    {#each [...headers] as [key, value]}
        <Header {key} {value} on:remove={(e) => removeHeader(e.detail)} />
    {/each}
    <h3 class="text-1xl font-normal leading-normal my-4 text-slate-800">Body</h3>
    <Body bind:value={rawBody} />
    <button
        class="border rounded border-gray-400 p-2 w-full hover:bg-slate-800 hover:text-teal-400"
        on:click={submit}>SUBMIT</button
    >
</main>
