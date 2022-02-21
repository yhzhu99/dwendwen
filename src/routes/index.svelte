<script>
  import SearchBar from "./components/SearchBar.svelte";
  import { onMount } from "svelte";

  let showBingDwenDwen = true
  let w,h

  onMount(async () => {
    w = document.documentElement.clientWidth
    h = document.documentElement.clientHeight
    showBingDwenDwen = true ? w/h > 1.4 : false

    let zoomW = mainCanvas.width / w;
    let zoomH = mainCanvas.height / h;
    zoomW = 1 / zoomW;
    zoomH = 1 / zoomH;
    zoomW = Math.floor(zoomW * 100) * 0.01 - 0.05;
    zoomH = Math.floor(zoomH * 100) * 0.01 - 0.05;

    let zoom = Math.min(zoomW, zoomH);
    mainCanvas.style.zoom = zoom;

    StyleKitName.drawCanvas1("mainCanvas");
  });
</script>

<svelte:head>
  <meta charset="UTF-8" />
  <meta name="keywords" content="墩墩起始页,主页,导航,起始页,朱英豪" />
  <meta
    name="description"
    content="墩墩起始页由朱英豪开发,冰墩墩主题,整合了多个学术搜索引擎,便捷好用,一起向未来!"
  />
  <title>墩墩起始页</title>
</svelte:head>

<main class="flex items-center flex-col justify-center min-h-screen bg-sky-500/[.5]">
  <div class="flex items-center mb-5">

    {#if showBingDwenDwen}
      <canvas height="1262" id="mainCanvas" width="1068" class="mr-5"
        >Your browser does not support the HTML5 CANVAS tag!</canvas
      >
    {/if}

    <div class="ml-5">
      <div
        class="font-mono text-2xl mb-5 font-bold text-slate-50 underline decoration-dashed"
      >
        Together for a Shared Future
      </div>
      <SearchBar />
    </div>
  </div>

  <footer class="place-self-end mr-5">
    <div class="text-center p-2 text-white text-sm font-mono rounded bg-sky-500/[.2]">
      <span>© 2022 Copyright: </span>
      <a href="https://github.com/TualatinX">Yinghao Zhu</a>
    </div>  
  </footer>
</main>
