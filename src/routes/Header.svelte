<div class="card-container">
  <h1 class="title">
    <a href="/" style="text-decoration: none; color: white">Page Maker</a>
  </h1>
  <div class="actions">
    <a href="/about" class="nav-button">About</a>
  </div>
</div>

<style>
  .card-container {
    width: 100%;
    height: 100px;
    background-color: #202020;
    position: absolute;
    top: 10px;
    left: 0;
    border: 1px solid black;
    border-radius: 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .title {
    margin-left: 20px;
  }

  .actions {
    display: flex;
    margin-right: 20px;
  }

  .nav-button {
    text-decoration: none;
    color: white;
    font-size: 20px;
    padding: 10px 20px;
    background-color: transparent;
    border-radius: 10px;
  }

  .nav-button:hover {
    background-color: black;
  }
</style>
