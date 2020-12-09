<script lang="ts">
import Card from "$components/Card.svelte";
import LayoutWithHeader from "$components/LayoutWithHeader.svelte";

export let cards: { header: string; value: string }[] = [
    {
        header: "Balance",
        value: "$99,999.99"
    },
    {
        header: "Sales",
        value: "999"
    },
    {
        header: "Messages",
        value: "999"
    }
];
export let posts;
</script>

<LayoutWithHeader>
    <div slot="header">Anon Anonov</div>

    <div slot="content">
        <div class="px-4 mx-auto max-w-6xl sm:px-6 lg:px-8">
            <h2 class="text-lg font-medium leading-6 text-cool-gray-900">Overview</h2>
            <div class="grid grid-cols-1 gap-5 mt-2 sm:grid-cols-2 lg:grid-cols-3">
                {#each cards as { header, value }}
                    <Card header="{header}" value="{value}" />
                {/each}
            </div>
        </div>
    </div>
</LayoutWithHeader>
