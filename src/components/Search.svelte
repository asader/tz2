<script>
import { onMount } from "svelte";

let posts = [];
let input;
let suggestions;
let searchValue = "";
let isSuggestionsVisible = false;

$: suggestionList = posts
    .map(({ title }) => title)
    .filter((title) => title.toLowerCase().includes(searchValue.toLowerCase()))
    .slice(0, 10);

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

<div class="flex relative flex-col flex-1">
    <div class="flex h-full text-gray-400 border-r md:ml-0 focus-within:text-gray-600">
        <input
            bind:this="{input}"
            bind:value="{searchValue}"
            on:input="{({ target }) => setSearchValue(target.value)}"
            class="flex py-2 px-3 w-full h-full placeholder-gray-500 text-gray-900 focus:outline-none focus:placeholder-gray-400 sm:text-sm"
            placeholder="Search"
            type="text"
        />
    </div>

    {#if suggestionList.length && isSuggestionsVisible}
        <div class="absolute z-40 mt-16 w-full bg-white rounded-md ring-1 ring-black ring-opacity-5 shadow-lg">
            <div class="py-1" role="menu" aria-orientation="vertical" aria-labelledby="options-menu">
                {#each suggestionList as suggestion}
                    <div
                        class="block py-2 px-4 text-sm text-gray-700 hover:bg-gray-100 hover:text-gray-900"
                        on:click="{() => setSearchValue(suggestion)}"
                        role="menuitem"
                    >
                        {suggestion}
                    </div>
                {/each}
            </div>
        </div>
    {/if}
</div>
