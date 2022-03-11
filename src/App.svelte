<script lang="ts">
    import Form from './Form.svelte';
    import Output from './Output.svelte';

    let promise: Promise<Response> = null;

    const sendRequest = (req: Request) => {
        promise = fetch(req);
    };

    const reset = () => {
        promise = null;
    };
</script>

<h1 class="text-3xl font-normal text-center leading-normal mt-0 mb-4 text-teal-400 bg-slate-800">
    Carta
</h1>
<main class="container mx-auto">
    <Form on:submit={(e) => sendRequest(e.detail)} />
    <Output bind:promise on:reset={reset} />
</main>
