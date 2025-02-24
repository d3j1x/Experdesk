<script lang="ts">
  import Versions from './components/Versions.svelte'
  import Theqcm from './components/Theqcm.svelte'
  import experdeskLogo from './assets/experdesk.png'

  const ipcHandle = (): void => window.electron.ipcRenderer.send('ping')
  const screenHandle = (): void => window.electron.ipcRenderer.send('resize-to-90')

  let x = true
  function handleClick() {
    x = !x
  }
</script>

{#if x}
  <img alt="logo" class="logo" src={experdeskLogo} />
  <div style="letter-spacing: 1px;" class="creator">
    Powered by <span style="letter-spacing: 2px; font-weight: bold;">d3j1x</span>
  </div>
  <div class="text">
    Lancez votre carrière dans le
    <span class="svelte">Testing</span>
    avec
    <span class="ts">Experdesk</span>.
  </div>
  <div class="mt-4 mb-2">
    <button
      class="border-2 rounded border-white bg-blue-600 p-2 text-2xl font-bold hover:bg-green-600"
      on:click={() => {
        handleClick()
        screenHandle()
      }}>Commencer Le QUIZ</button
    >
  </div>
  <p class="tip hidden">Please try pressing <code>F12</code> to open the devTool</p>
  <div class="actions">
    <div class="action text-lime-500">
      <a href="https://www.experdesk.tn/" target="_blank" rel="noreferrer">Explorer Experdesk</a>
    </div>
    <div class="action hidden">
      <!-- svelte-ignore a11y-click-events-have-key-events a11y-no-static-element-interactions a11y-missing-attribute-->
      <a target="_blank" rel="noreferrer" on:click={ipcHandle}>Send IPC</a>
    </div>
  </div>
  <Versions />
{:else}
  <div class="fixed top-4 left-4 text-xl font-mono text-red-500">
    <button class="font-extrabold" on:click={handleClick}>Quitter</button>
  </div>
  <div class="mx-auto justify-center items-center max-w-6xl">
    <Theqcm />
  </div>
{/if}
