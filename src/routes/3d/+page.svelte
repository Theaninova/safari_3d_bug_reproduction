<article>
  <h1>
    3D
  </h1>

  <div class="container">
    <section>
      <h2>No pseudo elements</h2>
      <div class="depth-container scroll">
        <div class="rotate-1">div</div>
        <div class="rotate-2">div</div>
        <div class="long"></div>
      </div>
    </section>
    <section>
      <h2>With one pseudo element</h2>
      <div class="depth-container scroll pseudo">
        <div class="rotate-1">div</div>
        <div class="long"></div>
      </div>
    </section>
  </div>
</article>

<style lang="scss" global>
  :root {
    overflow: hidden;
  }

  .container {
    display: flex;
    gap: 8px;
  }

  .scroll {
    overflow-y: scroll;
  }

  .long {
    height: 400px;
  }

  .depth-container {
    outline: 1px solid black;

    height: 300px;
    width: 300px;

    perspective: 100px;
    transform-style: preserve-3d;
  }

  .pseudo::after {
    content: '::after';
  }

  .rotate-1, .rotate-2, .pseudo::after {
    opacity: 0.8;

    position: absolute;
    top: 100px;
    left: 100px;

    width: 100px;
    height: 100px;
  }

  .rotate-1 {
    background-color: red;
    transform: rotate3d(0, 1, 0, 30deg);
  }

  .pseudo::after,
  .rotate-2 {
    background-color: green;
    transform: rotate3d(0, 1, 0, -30deg);
  }
</style>