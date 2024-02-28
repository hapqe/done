<script>
    import { flip } from "svelte/animate";
    import { dndzone } from "svelte-dnd-action";
    const flipDurationMs = 150;
    export let name;
    export let items;
    export let onDrop;

    function handleDndConsiderCards(e) {
        console.warn("got consider", name);
        items = e.detail.items;
    }
    function handleDndFinalizeCards(e) {
        onDrop(e.detail.items);
    }
</script>

<div class="wrapper">
    <div class="column-title">
        {name}
    </div>
    <div
        class="column-content"
        use:dndzone={{ items, flipDurationMs, zoneTabIndex: -1 }}
        on:consider={handleDndConsiderCards}
        on:finalize={handleDndFinalizeCards}
    >
        {#each items as item (item.id)}
            <div class="card" animate:flip={{ duration: flipDurationMs }}>
                <p contenteditable>{item.name}</p>
            </div>
        {/each}
    </div>
</div>

<style>
    .wrapper {
        height: 100%;
        width: 100%;
        /*Notice we make sure this container doesn't scroll so that the title stays on top and the dndzone inside is scrollable*/
        overflow-y: hidden;
    }
    .column-content {
        height: calc(100% - 2.5em);
        /* Notice that the scroll container needs to be the dndzone if you want dragging near the edge to trigger scrolling */
        min-height: 1em;
        padding: 1em;
        padding-top: 0.2em;
    }
    .column-title {
        font-weight: bold;
        padding-left: 1em;
    }
    .card {
        padding: 0.5em;
        width: 100%;
        margin: 0.4em 0;
        border-radius: 0.5em;
        background-color: var(--primary);
    }

    p {
        width: fit-content;
        outline: none;
        color: var(--bg);
    }

    [contenteditable] {
        -webkit-user-select: text;
    }
</style>
