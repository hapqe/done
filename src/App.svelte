<script>
  import Board from "./lib/Board.svelte";
  import Title from "./lib/Title.svelte";
  let columnsData = [
    {
      id: "c1",
      name: "TODO",
      items: [
        { id: 1, name: "item41" },
        { id: 9, name: "item49" },
      ],
    },
    {
      id: "c2",
      name: "DOING",
      items: [
        { id: 10, name: "item50" },
        { id: 11, name: "item51" },
      ],
    },
    {
      id: "c3",
      name: "DONE",
      items: [{ id: 13, name: "item52" }],
    },
  ];
  function handleBoardUpdated(newColumnsData) {
    // if you wanted to update a database or a server, this is where you would do it
    columnsData = newColumnsData;
  }
</script>

<Title />
<Board columns={columnsData} onFinalUpdate={handleBoardUpdated} />

<style>
  :global(*) {
    box-sizing: border-box;
    margin: 0;
  }
</style>
