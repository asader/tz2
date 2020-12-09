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
        <div class="flex fixed inset-0 z-40">
            <div class="absolute inset-0 bg-gray-600 opacity-75"></div>

            <div class="flex relative flex-col flex-auto pt-5 pb-4 w-full max-w-xs bg-green-400">
                <div class="overflow-y-auto mt-5">
                    <nav class="px-2 space-y-1">
                        {#each links as { s, t }}
                            <SideBarLink href="{`/${s}`}" current="{path === s}">{t}</SideBarLink>
                        {/each}
                    </nav>
                </div>
            </div>
            <button
                on:click="{() => (isSidebarVisible = false)}"
                class="flex relative flex-grow h-full focus:bg-gray-600"
                aria-label="Close sidebar"
            >
                <svg class="m-4 w-12 h-12 text-white" stroke="currentColor" fill="none" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                </svg>
            </button>
        </div>
    {/if}
</div>

<div class="hidden lg:flex lg:flex-shrink-0">
    <div class="flex overflow-y-auto flex-col flex-grow py-4 w-64 bg-green-400">
        <div class="flex overflow-y-auto flex-col flex-1 mt-5">
            <div class="overflow-y-auto">
                <nav class="px-2 space-y-1">
                    {#each links as { s, t }}
                        <SideBarLink href="{`/${s}`}" current="{path === s}">{t}</SideBarLink>
                    {/each}
                </nav>
            </div>
        </div>
    </div>
</div>
