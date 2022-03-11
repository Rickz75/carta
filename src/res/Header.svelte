<script lang="ts">
    export let key: string;
    export let value: string;
</script>

<div class="flex items-stretch my-2 border rounded border-gray-400">
    <div class="w-5/12 p-2 border-r border-white">
        {key}
    </div>
    <div class="w-5/12 p-2 border-r border-white">
        {value}
    </div>
</div>
