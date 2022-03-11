<script lang="ts">
    export let value: string;

    let proto = 'https://';
    let addr = '';

    const prependProtocol = () => {
        value = `${proto}${addr}`;
    };

    const switchProtocol = () => {
        proto = proto === 'https://' ? 'http://' : 'https://';
        prependProtocol();
    };
</script>

<button
    class="btn w-2/12 p-2 bg-slate-800 text-teal-300 hover:bg-slate-900"
    on:click={switchProtocol}
>
    {proto}
</button>
<input
    class="w-8/12 p-2 outline-none"
    type="text"
    placeholder="localhost:8080"
    bind:value={addr}
    on:change={prependProtocol}
/>
