<script lang="ts">
    export let value: string;
</script>

<select class="w-2/12 bg-slate-800 p-2 text-center text-teal-300" bind:value>
    <option value="GET">GET</option>
    <option value="POST">POST</option>
    <option value="PATCH">PATCH</option>
    <option value="PUT">PUT</option>
    <option value="DELETE">DELETE</option>
    <option value="HEAD">HEAD</option>
    <option value="CONNECT">CONNECT</option>
    <option value="OPTIONS">OPTIONS</option>
    <option value="TRACE">TRACE</option>
</select>
