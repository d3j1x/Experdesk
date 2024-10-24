<script lang="ts">
  import Versions from './components/Versions.svelte'
  import Theqcm from './components/Theqcm.svelte'
  import experdeskLogo from './assets/experdesk.png'

  const ipcHandle = (): void => window.electron.ipcRenderer.send('ping')
  let x = true
  function handleClick() {
    x = !x
  }
</script>

{#if x}
  <img alt="logo" class="logo" src={experdeskLogo} />
  <div style="letter-spacing: 1px;" class="creator">
    Powered by <span style="letter-spacing: 2px; font-weight: bold;">EXPERTEAM</span>
  </div>
  <div class="text">
    Lancez votre carrière dans le
    <span class="svelte">Testing</span>
    avec
    <span class="ts">Expertest</span>.
  </div>
  <div class="my-2">
    <button
      class="border-2 rounded border-white hover:bg-blue-600 p-2 text-3xl font-bold bg-black"
      on:click={handleClick}>START THE QCM</button
    >
  </div>
  <p class="tip hidden">Please try pressing <code>F12</code> to open the devTool</p>
  <div class="actions">
    <div class="action">
      <a href="https://www.expertest.tn/" target="_blank" rel="noreferrer">Documentation</a>
    </div>
    <div class="action">
      <!-- svelte-ignore a11y-click-events-have-key-events a11y-no-static-element-interactions a11y-missing-attribute-->
      <a target="_blank" rel="noreferrer" on:click={ipcHandle}>Send IPC</a>
    </div>
  </div>
  <Versions />
{:else}
  <div class="fixed top-4 left-4 text-xl font-mono text-red-500">
    <button class="" on:click={handleClick}>Back</button>
  </div>
  <Theqcm />
{/if}
