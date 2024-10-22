<script lang="ts">
  import Versions from './components/Versions.svelte'
  import experdeskLogo from './assets/experdesk.png'

  const ipcHandle = (): void => window.electron.ipcRenderer.send('ping')
</script>

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
<p class="tip">Please try pressing <code>F12</code> to open the devTool</p>
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
