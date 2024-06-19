<script>
  import Footer from "./Footer.svelte";
  import Header from "./Header.svelte";
  import "./styles.css";
</script>

<div class="container">
  <Header />
  <main class="content">
    <slot />
  </main>
  <Footer />
</div>

<style>
  .container {
    width: 100%;
    min-height: 100vh;
    position: relative;
    display: flex;
    flex-direction: column;
  }
  .content {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  main {
    flex: 1;
    display: flex;
    flex-direction: column;
    padding: 1rem;
    width: 100%;
    max-width: 64rem;
    margin: 0 auto;
    box-sizing: border-box;
  }
</style>
