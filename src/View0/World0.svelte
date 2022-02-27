<script lang="ts">
  export let viewHeight;
  export let viewWidth;
  import { width, height } from "../stores";
  import Bob0 from "./Bob0.svelte";
  import Path from "../Path.svelte";

  let extremePoints = [
    [-1000000, 0],
    [1000000, 0],
    [0, -1000000],
    [0, 1000000],
  ];
</script>

<svg
  viewBox="0 {-viewHeight} {viewWidth} {viewHeight * 1.5}"
  width="100%"
  height="200"
  style="background-color:lightgray"
>
  <Path path={[extremePoints[0], extremePoints[1]]} color="grey" />
  <Path path={[extremePoints[2], extremePoints[3]]} color="grey" />
  <slot><Bob0 /></slot>
</svg>
