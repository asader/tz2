<script lang="ts">
	import Card from "$components/Card.svelte";
	import LayoutWithHeader from "$components/LayoutWithHeader.svelte";

	export let cards: { header: string; value: string }[] = [
      {
          header: 'Balance',
          value: '$99,999.99',
      },
      {
          header: 'Sales',
          value: '999',
      },
      {
          header: 'Messages',
          value: '999',
      }
	];
	export let posts;
</script>

<LayoutWithHeader>
    <div slot="header">Anon Anonov</div>

		<div slot="content">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="text-lg leading-6 font-medium text-cool-gray-900">Overview</h2>
            <div class="mt-2 grid grid-cols-1 gap-5 sm:grid-cols-2 lg:grid-cols-3">
							{#each cards as { header, value }}
                  <Card {header} {value}/>
							{/each}
            </div>
        </div>
		</div>
</LayoutWithHeader>
