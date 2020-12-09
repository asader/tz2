<script>
		import Search from "$components/Search.svelte";

		export let isSidebarVisible;
</script>

<div class="relative flex h-16 bg-white border-b border-gray-200">
    <button on:click={() => isSidebarVisible = true} class="px-4 border-r border-gray-200 text-gray-400 focus:outline-none focus:bg-gray-100 focus:text-gray-600 lg:hidden" aria-label="Open sidebar">
        <svg class="block h-6 w-6" stroke="currentColor" fill="none" viewBox="0 0 24 24">
		        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
        </svg>
    </button>
    <div class="flex-1 flex justify-between sm:px-6 lg:max-w-6xl lg:mx-auto lg:px-8">
        <Search/>


        <button class="px-4 text-gray-400 hover:bg-gray-100 hover:text-gray-500 focus:outline-none">
            Log out
        </button>
    </div>
</div>
