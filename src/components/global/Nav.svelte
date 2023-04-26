<script>
  import { page } from "$app/stores";
  import FaGithub from "svelte-icons/fa/FaGithub.svelte";
  const navItems = [
    { name: "Components", url: "/components" }
  ];
</script>

<style>
  .active {
    text-decoration: underline;
  }
  .icon {
    color: #fff;
    width: 1.3em;
    height: 1.3em;
    display: inline-block;
    vertical-align: middle;
  }
</style>

<nav class="flex items-center justify-between flex-wrap">
    <div class="flex items-center flex-shrink-0 text-white mr-9">
      <a href="/"><span class="font-semibold text-xl tracking-tight text-xl">APG Svelte Components</span></a>
    </div>
    <div class="block lg:hidden">
      <button class="flex items-center px-3 py-2 border rounded text-white border-teal-400 hover:text-white hover:border-white">
        <svg class="fill-current h-3 w-3" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><title>Menu</title><path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z"/></svg>
      </button>
    </div>
    <div class="w-full block flex-grow lg:flex lg:items-center lg:w-auto">
      <div class="text-sm lg:flex-grow">
        {#each navItems as item}
          <a href={item.url} class="block mt-4 lg:inline-block lg:mt-0 text-white hover:underline mr-4 text-lg" class:active={$page.route.id === item.url} aria-current={$page.route.id === item.url ? "page" : null}>{item.name}</a>
        {/each}
      </div>
      <div>
        <a href="#" class="inline-block text-sm px-4 py-2 leading-none border rounded text-white border-white mt-4 lg:mt-0">
          <span class="icon"><FaGithub /></span>
          GitHub
        </a>
      </div>
    </div>
  </nav>