<script lang="ts">
import SideBar from "$components/SideBar/SideBar.svelte";
import Navbar from "$components/Navbar.svelte";

export let segment: string;

let isSidebarVisible = false;
const links = [
    { s: "", t: "Profile" },
    { s: "#", t: "Settings" },
    { s: "#", t: "Log out" }
];
import "$styles/global.css";
</script>

<div class="flex h-screen">
    <SideBar bind:isSidebarVisible links="{links}" segment="{segment}" />
    <div class="overflow-auto flex-1 focus:outline-none" tabindex="0">
        <Navbar bind:isSidebarVisible />
        <main class="overflow-y-auto relative z-0 flex-1 pb-8">
            <div class="bg-white shadow">
                <div class="py-6 px-4 sm:px-6 lg:max-w-6xl lg:mx-auto lg:px-8">
                    <div class="flex-1 min-w-0">
                        <div class="flex items-center">
                            <h1 class="ml-3 text-2xl font-bold leading-7 text-cool-gray-900 sm:leading-9 sm:truncate">
                                <slot name="header">Unknown header</slot>
                            </h1>
                        </div>
                    </div>
                </div>
            </div>

            <div class="mt-8">
                <slot name="content"><span>Unknown content</span></slot>
            </div>
        </main>
    </div>
</div>
