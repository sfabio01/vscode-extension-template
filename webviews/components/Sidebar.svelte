<script lang="ts">
    import { onMount } from "svelte";

    let text = "";

    function fetchText() {
        // send message to the extension asking for the selected text
        tsvscode.postMessage({ type: "onFetchText", value: "" });
    }

    onMount(() => {
        // Listen for messages from the extension
        window.addEventListener("message", (event) => {
            const message = event.data;
            switch (message.type) {
                case "onSelectedText": {
                    text = message.value;
                    break;
                }
            }
        });
    });
</script>

<h1>Sidebar Panel</h1>
<label for="text"><b>Selected text</b></label>
<textarea
    rows="15"
    id="text"
    style="resize: vertical;"
    minlength="30"
    bind:value={text}
/>
<button on:click={fetchText}>fetch text</button>
