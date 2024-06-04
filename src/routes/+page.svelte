<script lang="ts">
  import { writable } from "svelte/store";

  let isReady: boolean = false;
  const file = writable<File | undefined>(undefined);
  let errorMessage: string | null = null;
  let fileInput: HTMLInputElement;

  function handleSubmit() {
    if (!isReady) return console.log("not ready");
    console.log("Ready to submit ", file);
  }

  function handleLoad(
    event: Event & {
      currentTarget: EventTarget & HTMLInputElement;
    }
  ) {
    if (event.target instanceof HTMLInputElement && event.target.files) {
      const zipRegex = /\.zip$/;
      if (!zipRegex.test(event.target.files[0].name)) {
        errorMessage = "File must be a zip file";
        return;
      } else {
        errorMessage = null;
      }
      const eventInput = event.target.files[0];
      file.set(eventInput);
    }
    isReady = true;
  }

  function handleReset() {
    isReady = false;
    file.set(undefined);
    errorMessage = null;
    fileInput.value = "";
  }
</script>

<div class="container">
  <h1>Drop your files here</h1>
  <div class="input-wrapper">
    <input
      type="file"
      accept=".zip"
      bind:value={$file}
      bind:this={fileInput}
      class="input-field"
      class:active-read={isReady}
      id=""
      on:input={(e) => handleLoad(e)}
    />
    <button class="reset-button" on:click={() => handleReset()}>X</button>
  </div>
  {#if errorMessage}
    <p class="error-message">{errorMessage}</p>
  {/if}
  {#if isReady}
    <button class="action-button" on:click={() => handleSubmit()}>
      Generate
    </button>
  {/if}
</div>

<style>
  .container {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 20px 0;
  }

  .input-wrapper {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .input-field {
    background-color: transparent;
    padding: 20px;
    border: 1px solid black;
    border-top-left-radius: 10px;
    border-bottom-left-radius: 10px;
    border-right: transparent;
  }

  .reset-button {
    padding: 20px;
    background-color: red;
    font-size: large;
    color: white;
    border: 1px solid black;
    border-left: transparent;
    border-top-right-radius: 10px;
    border-bottom-right-radius: 10px;
    cursor: pointer;
  }

  .action-button {
    width: 40%;
    height: 100px;
    padding: 10px 20px;
    background-color: #202020;
    font-size: large;
    color: white;
    border: 1px solid black;
    border-radius: 10px;
    cursor: pointer;
  }

  .action-button:hover {
    background-color: black;
    color: white;
  }

  .active-read {
    border: 1px solid blue;
  }

  .error-message {
    color: red;
  }
</style>
