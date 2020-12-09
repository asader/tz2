<script lang="ts">
  import SideBarLink from "./SideBarLink";

  export let links: { s: string; t: string }[];
  export let segment: string;
  export let isSidebarVisible: boolean = false;

  //segment might be undefined, so we use path to be a empty string
  let path: string;
  $: path = segment || "";
</script>

<div class="lg:hidden">
	{#if isSidebarVisible}
    <div class="fixed inset-0 flex z-40">
        <div class="absolute inset-0 bg-gray-600 opacity-75"></div>

        <div class="relative flex-auto flex flex-col max-w-xs w-full pt-5 pb-4 bg-green-400">
            <div class="mt-5 overflow-y-auto">
                <nav class="px-2 space-y-1">
									{#each links as { s, t }}
                      <SideBarLink href={`/${s}`} current={path === s}>{t}</SideBarLink>
									{/each}
                </nav>
            </div>
        </div>
        <button on:click={() => isSidebarVisible = false} class="relative flex h-full flex-grow focus:bg-gray-600" aria-label="Close sidebar">
            <svg class="h-12 w-12 m-4 text-white" stroke="currentColor" fill="none" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
        </button>
      </div>
	{/if}
</div>


<div class="hidden lg:flex lg:flex-shrink-0">
    <div class="flex flex-col w-64 flex-grow bg-green-400 py-4 overflow-y-auto">
        <div class="mt-5 flex-1 flex flex-col overflow-y-auto">
            <div class="overflow-y-auto">
                <nav class="px-2 space-y-1">
									{#each links as { s, t }}
                      <SideBarLink href={`/${s}`} current={path === s}>{t}</SideBarLink>
									{/each}
                </nav>
            </div>
        </div>
    </div>
</div>
