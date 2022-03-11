<script lang="ts">
    import { onMount } from 'svelte';

    export let value: string;

    onMount(() => {
        (document.getElementById('body') as HTMLTextAreaElement).addEventListener(
            'keydown',
            function (e: any) {
                if (e.key == 'Tab') {
                    e.preventDefault();
                    var start = this.selectionStart;
                    var end = this.selectionEnd;

                    this.value = this.value.substring(0, start) + '\t' + this.value.substring(end);

                    this.selectionStart = this.selectionEnd = start + 1;
                }
            }
        );
    });
</script>

<textarea
    id="body"
    class="w-full bg-slate-800 p-2 mt-0 my-2 text-gray-200 outline-none border border-transparent rounded focus:border-teal-400"
    rows={6}
    bind:value
/>
