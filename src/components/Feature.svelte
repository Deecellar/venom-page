<script lang="ts">
    import FeatureClass from "./FeatureClass";

    export let goals: FeatureClass[] = [
        new FeatureClass(),
        new FeatureClass(),
        new FeatureClass(),
    ];
</script>

<div class="py-12 bg-white dark:bg-gray-800">
    <div class="max-w-xl mx-auto px-4 sm:px-6 lg:max-w-7xl lg:px-8">
        <h2 class="sr-only">Venom features</h2>
        <dl class="space-y-10 lg:space-y-0 lg:grid lg:grid-cols-3 lg:gap-8">
            {#each goals as goal}
                <div>
                    <dt>
                        <div
                            class="flex items-center justify-center h-12 w-12 rounded-md bg-green-500 text-white"
                        >
                            <!-- Heroicon name: outline/globe-alt -->
                            <svg
                                class="h-6 w-6"
                                xmlns="http://www.w3.org/2000/svg"
                                fill="none"
                                viewBox="0 0 24 24"
                                stroke="currentColor"
                                aria-hidden="true"
                            >
                                <path
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                    d="M5 13l4 4L19 7"
                                />
                            </svg>
                        </div>
                        <p
                            class="mt-5 text-lg leading-6 font-medium text-gray-900 dark:text-gray-50"
                        >
                            {#if goal.title.length == 0}
                                <div
                                    class="flex flex-col space-y-3 animate-pulse"
                                >
                                    <div
                                        class="w-32 bg-gray-300 h-4 rounded-md "
                                    />
                                </div>
                            {:else}
                                {goal.title}
                            {/if}
                        </p>
                    </dt>
                    <dd class="mt-2 text-base text-gray-500 dark:text-gray-200">
                        {#if goal.goal.length == 0}
                            <div
                                class="flex flex-col space-y-3 animate-pulse mt-2 "
                            >
                                <div class="w-50 bg-gray-300 h-4 rounded-md " />
                            </div>
                        {:else}
                            <p>{goal.goal}</p>
                        {/if}
                    </dd>
                </div>
            {/each}
        </dl>
    </div>
</div>
