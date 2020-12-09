<script>
  import { onMount } from 'svelte';

	let posts = [];
	let input;
	let suggestions;
	let searchValue = "";
	let isSuggestionsVisible = false;

  $: suggestionList = posts
      .map(({ title }) => title)
      .filter(title => title.toLowerCase().includes(searchValue.toLowerCase())).slice(0, 10);

  onMount(async () => {
      const res = await fetch(`https://jsonplaceholder.typicode.com/posts`);
      posts = await res.json();
      document.onclick = (e) => {
        isSuggestionsVisible = input === e.target;
      };
  });

	const setSearchValue = (val) => {
    searchValue = val;
  };

</script>

<div class="flex-1 flex flex-col relative">
	<div class="md:ml-0 flex text-gray-400 focus-within:text-gray-600 border-r h-full">
		<input
      bind:this={input}
      bind:value={searchValue}
		  on:input={({target}) => setSearchValue(target.value)}
		  class="flex w-full h-full px-3 py-2 text-gray-900 placeholder-gray-500 focus:outline-none focus:placeholder-gray-400 sm:text-sm"
		  placeholder="Search"
		  type="text"
		>
	</div>

	{#if suggestionList.length && isSuggestionsVisible}
    <div class="absolute mt-16 w-full rounded-md shadow-lg bg-white ring-1 ring-black ring-opacity-5 z-40">
      <div class="py-1" role="menu" aria-orientation="vertical" aria-labelledby="options-menu">
				{#each suggestionList as suggestion}
			    <div
						class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 hover:text-gray-900"
						on:click={() => setSearchValue(suggestion)} role="menuitem"
			    >{suggestion}</div>
				{/each}
      </div>
    </div>
	{/if}
</div>
