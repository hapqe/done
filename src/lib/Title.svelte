<script>
    import pen from "../assets/pen.svg";

    console.log(pen);

    const date = new Date(Date.now());
    const options = {
        year: "2-digit",
        month: "numeric",
        day: "numeric",
    };
</script>

<div>
    <h1>{date.toLocaleDateString("de-DE", options)}</h1>
    <button style="mask: url({pen}) no-repeat center"></button>
</div>

<style>
    div {
        margin: 1em;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    button {
        border: none;
        background: none;
        cursor: pointer;
        transition: transform 0.3s;
        width: 2em;
        height: 2em;

        background: var(--primary);
    }
    button:hover {
        transform: scale(1.1);
    }
</style>
