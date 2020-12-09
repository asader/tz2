<script lang="ts">
    export let header: string;
    export let value: string;
</script>

<div class="bg-white overflow-hidden shadow rounded-lg">
    <div class="p-5">
        <div class="flex items-center">
            <div class="ml-5 w-0 flex-1">
                <dl>
                    <dt class="text-sm leading-5 font-medium text-cool-gray-500 truncate">{header}</dt>
                    <dd>
                        <div class="text-lg leading-7 font-medium text-cool-gray-900">{value}</div>
                    </dd>
                </dl>
            </div>
        </div>
    </div>
</div>
