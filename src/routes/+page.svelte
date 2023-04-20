<div class="scroll">
  <div class="parallax">
    <article>
      <h1>Welcome to SvelteKit</h1>
      {#each Array.from({length: 10}) as _}
        <button on:click={() => alert("Click!")}>Click me!</button>
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore
        magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
        consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla
        pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est
        laborum.
      </p>
        {/each}
    </article>
  </div>
</div>

<style lang="scss">
  $parallax-background: gray;
  $background: black;
  $parallax-strength: 2;
  $overscroll-padding: 720px;
  $content-size: 230px;

  :global(:root) {
    font-family: sans-serif;
    overflow: hidden;
  }

  :global(body) {
    margin: 0;
    background: $background;
  }

  .scroll {
    height: 200vh;
    overflow-y: auto;
    overflow-x: hidden;

    perspective: 2px;
    perspective-origin: center top;
  }

  .parallax {
    transform-style: preserve-3d;
    position: relative;

    &::after {
      content: ' ';
      position: absolute;
      top: 0;
      right: 0;
      left: 0;

      $height: calc($content-size + $overscroll-padding);
      $translateY: calc($overscroll-padding * $parallax-strength);
      $translateZ: calc(-1px * $parallax-strength);
      $transform-origin: calc($parallax-strength * $parallax-strength * $overscroll-padding);

      height: $height;
      width: 150%;
      transform-origin: 50% $transform-origin;
      translate: 0px $translateY $translateZ;
      scale: $parallax-strength;
      z-index: -1;

      background: $parallax-background;
    }
  }

  article {
    margin-block: 50px;
    margin-inline: 64px;
    padding: 16px;
    background: rgba(255, 255, 255, 0.7);
    height: 500vh;
  }
</style>
