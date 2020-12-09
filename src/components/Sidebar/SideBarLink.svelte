<script lang="ts">
export let href: string;
export let current: boolean;

const general: string =
    "group flex items-center px-2 py-2 text-base leading-6 font-medium rounded-md transition ease-in-out duration-150";
const active: string = "text-white bg-green-700 focus:outline-none focus:bg-green-500";
const inactive: string = "text-green-100 hover:text-white hover:bg-green-500 focus:outline-none focus:bg-green-500";
</script>

<a rel="prefetch" href="{href}" class="{general} {current ? active : inactive}"><slot /></a>
