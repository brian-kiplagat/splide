<script lang="ts">
  import viteLogo from "/vite.svg";

  import Splide from "@splidejs/splide";
  import { AutoScroll } from "@splidejs/splide-extension-auto-scroll";
  import { onMount } from "svelte";

  let items = Array.from({ length: 10 }, (_, i) => i + 1);

  onMount(() => {
    const element = document.querySelector("#splide") as HTMLElement;
    console.log({ element });
    const splide = new Splide(element, {
      type: "loop",
      drag: "free",
      focus: "center",
      direction: "ltr",
      gap: "1rem",
      arrows: false,
      pagination: false,
      perPage: 3,
      autoScroll: {
        speed: 2,
        pauseOnFocus: true,
        pauseOnHover: true,
      },
    });

    splide.mount({ AutoScroll });
  });
</script>

<main>
  <div id="splide" class="splide" aria-label="Marquee Slider">
    <div class="splide__track">
      <div class="splide__list">
        <!-- Example list items with links and images -->
        {#each items as item}
          <div class="splide__slide">
            <img src={viteLogo} class="logo svelte" alt="alternative" />
          </div>
        {/each}
        <!-- Add more slides as needed -->
      </div>
    </div>
  </div>
</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
</style>
