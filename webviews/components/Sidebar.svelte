<script lang="ts">
    import { onMount } from "svelte";

    onMount(() => {
        // Listen for messages from the extension
        window.addEventListener("message", (event) => {
            const message = event.data;
            switch (message.type) {
                case "onSomething": {
                    // code here...
                    break;
                }
            }
        });
    });
</script>

<h1>Sidebar Panel</h1>
