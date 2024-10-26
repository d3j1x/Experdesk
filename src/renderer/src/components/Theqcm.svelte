<script>
  import Scrum from './scrum/Scrum.svelte'
  let x = true
  function handleClick() {
    x = !x
  }
</script>

<div class="grid-flow-row bg-white text-black p-4 rounded max-w-7xl">
  {#if x}
    <div class="py-10 px-5 bg-slate-300 rounded">
      <h1 class="text-4xl font-semibold">Bonjour, veuillez choisir le module du QCM :</h1>
      <div class="justify-center items-center">
        <button
          class="flex mt-10 mx-auto text-3xl border-4 rounded border-blue-700 hover:bg-blue-600 bg-blue-300 text-black font-bold p-2"
          on:click={handleClick}>Scrum Agile v2020</button
        >
      </div>
    </div>
  {:else}
    <Scrum />
  {/if}
</div>
