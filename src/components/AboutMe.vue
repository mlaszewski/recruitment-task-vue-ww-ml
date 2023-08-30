<template>
  <div class="section about" id="about">
    <div class="image-container">
      <img src="/images/tim-bogdanov-4uojMEdcwI8-unsplash.png" alt="about image" />
    </div>
    <div class="content">
      <h2 class="section-header">O MNIE</h2>
      <p class="content-section">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>

      <p class="content-section">Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>

      <p class="content-section">Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt.</p>

      <p class="content-section">Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam.</p>

    </div>
  </div>
</template>

<style lang="scss">
.about {
  display: flex;
  align-items: center;
  margin: 8em 0 4em 0;
  @media (max-width: $medium) {
    flex-direction: column-reverse;
    height: 100%;

    .section-header {
      text-align: center;
    }
    .image-container {
      height: 100%;
      z-index: -1;
    }
  }

  .image-container {
    height: 80%;
    flex: 5;
    display: flex;
    align-items: flex-end;
    overflow: hidden;
  }

  .content {
    flex: 2;
    padding: 0 10%;

    .content-section {
      margin: 0 0 1em 0;
    }

    @media (max-width: $medium) {
      flex: auto;
      margin-bottom: 2em;
    }
  }
}
</style>