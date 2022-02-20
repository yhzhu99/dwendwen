<script>
  // import { goto } from "$app/navigation";
  let searchEngines = [
    { id: 1, text: `Google`, url: "https://www.google.com.hk/search?q=", home: "https://www.google.com.hk"},
    { id: 2, text: `Bing`, url: "https://cn.bing.com/search?q=" , home:"https://cn.bing.com"},
    { id: 3, text: `Baidu`, url: "https://www.baidu.com/s?ie=utf-8&word=", home: "https://www.baidu.com"},
    { id: 4, text: `Google Scholar`, url: "https://scholar.google.com/scholar?q=", home: "https://scholar.google.com"},
    { id: 5, text: `GitHub`, url: "https://github.com/search?q=", home: "https://github.com"},
    { id: 6, text: `arXiv`, url: "https://arxiv.org/search/?searchtype=all&source=header&query=",  home: "https://arxiv.org"},
    { id: 7, text: `ReadPaper`, url: "https://readpaper.com/search/", home: "https://readpaper.com"},
  ];
  let selected;
  let question = "";
  function handleSearch() {
    if (question.trim() == []) {
      window.open(selected.home)
      // goto(selected.home);
    } else{
      window.open(selected.url + question)
      // goto(selected.url + question);
    }
  }
</script>

<form
  class=" bg-white rounded flex items-center p-3 shadow-sm border border-gray-200"
  on:submit|preventDefault={handleSearch}
>
  <button class="outline-none focus:outline-none" type="submit"
    ><svg
      class="w-5 text-gray-600 h-5 cursor-pointer"
      fill="none"
      stroke-linecap="round"
      stroke-linejoin="round"
      stroke-width="2"
      stroke="currentColor"
      viewBox="0 0 24 24"
      ><path d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" /></svg
    ></button
  >
  <input
    bind:value={question}
    type="search"
    placeholder="Search"
    class="w-80 pl-4 text-sm outline-none focus:outline-none bg-transparent"
  />

  <select
    class="text-sm outline-none focus:outline-none bg-transparent"
    bind:value={selected}
  >
    {#each searchEngines as engine}
      <option value={engine}>
        {engine.text}
      </option>
    {/each}
  </select>
</form>
