<script lang="ts">
export let header: string;
export let value: string;
</script>

<div class="overflow-hidden bg-white rounded-lg shadow">
    <div class="p-5">
        <div class="flex items-center">
            <div class="flex-1 ml-5 w-0">
                <dl>
                    <dt class="text-sm font-medium leading-5 text-cool-gray-500 truncate">{header}</dt>
                    <dd>
                        <div class="text-lg font-medium leading-7 text-cool-gray-900">{value}</div>
                    </dd>
                </dl>
            </div>
        </div>
    </div>
</div>
