<script lang="ts">
    import { Link } from "svelte-routing";
    import { select_option } from "svelte/internal";
    import Feature from "../components/Feature.svelte";
    import FeatureClass from "../components/FeatureClass";
    import Feed from "../components/Feed.svelte";
    import FeedItemClass from "../components/FeedItemClass";
    async function getFeed(): Promise<FeedItemClass[]> {
        const response = await fetch("data/announcements.djson");
        const items: FeedItemClass[] = await response.json();
        return items;
    }

    async function getFeatures(): Promise<FeatureClass[]> {
        const response = await fetch("data/features.djson");
        const items: FeatureClass[] = await response.json();
        return items;
    }
</script>

<section>
    <div>
        <div class="relative">
            <div
                class="absolute inset-x-0 bottom-0 h-1/2 bg-gray-800 dark:bg-gray-200"
            />
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div
                    class="relative shadow-xl sm:rounded-2xl sm:overflow-hidden"
                >
                    <div class="absolute inset-0">
                        <img
                            class="h-full w-full object-cover"
                            src="https://i.postimg.cc/pxyYPrJy/screenshot-20210312.png"
                            alt="Venom Linux Desktop Example"
                        />
                        <div
                            class="absolute inset-0 bg-gray-500 mix-blend-multiply"
                        />
                    </div>
                    <div
                        class="relative px-4 py-16 sm:px-6 sm:py-24 lg:py-32 lg:px-8"
                    >
                        <h1
                            class="text-center text-4xl font-extrabold font-inter   tracking-tight sm:text-5xl lg:text-6xl"
                        >
                            <span class="block   text-white"
                                >A lightweight source based distro for</span
                            >
                            <span
                                class="block   text-indigo-200 f   hover:text-indigo-400 transition-colors "
                                >advanced Linux Users</span
                            >
                        </h1>
                        <p
                            class="mt-6 max-w-lg  mx-auto text-center font-inter text-xl text-indigo-200 sm:max-w-3xl"
                        >
                            Customize your system with Venom Linux, a
                            lightweight source based distro for advanced Linux
                            users targeting x86_64 machines
                        </p>
                        <div
                            class="mt-10 max-w-sm mx-auto sm:max-w-none sm:flex sm:justify-center"
                        >
                            <div
                                class="space-y-4 sm:space-y-0 sm:mx-auto sm:inline-grid sm:grid-cols-2 sm:gap-5"
                            >
                                <Link
                                    to="wiki"
                                    class="flex items-center rounded-sm transition-colors justify-center px-4 py-3 border-transparent text-base font-medium border  shadow-sm text-blue-800 bg-white hover:bg-indigo-50 sm:px-8"
                                >
                                    Get started
                                </Link>
                                <Link
                                    to="downloads"
                                    class="flex items-center transition-colors rounded-sm justify-center px-4 py-3 border-transparent text-base font-medium borde  shadow-sm  text-white bg-indigo-500 bg-opacity-60 hover:bg-opacity-70 sm:px-8"
                                >
                                    Download now
                                </Link>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

<section id="Announcements" class="mt-5">
    <h3 class="dark:text-gray-200 text-xl ml-4 pl-1 mb-2  ">Announcements</h3>
    {#await getFeed()}
        <Feed />
    {:then val}
        <Feed items={val} />
    {:catch err}
        <!-- This example requires Tailwind CSS v2.0+ -->
        <div class="rounded-md bg-yellow-50 dark:bg-yellow-700 p-4">
            <div class="flex">
                <div class="flex-shrink-0">
                    <!-- Heroicon name: solid/exclamation -->
                    <svg
                        class="h-5 w-5 text-yellow-400"
                        xmlns="http://www.w3.org/2000/svg"
                        viewBox="0 0 20 20"
                        fill="currentColor"
                        aria-hidden="true"
                    >
                        <path
                            fill-rule="evenodd"
                            d="M8.257 3.099c.765-1.36 2.722-1.36 3.486 0l5.58 9.92c.75 1.334-.213 2.98-1.742 2.98H4.42c-1.53 0-2.493-1.646-1.743-2.98l5.58-9.92zM11 13a1 1 0 11-2 0 1 1 0 012 0zm-1-8a1 1 0 00-1 1v3a1 1 0 002 0V6a1 1 0 00-1-1z"
                            clip-rule="evenodd"
                        />
                    </svg>
                </div>
                <div class="ml-3">
                    <h3
                        class="text-sm font-medium text-yellow-800 dark:text-yellow-100"
                    >
                        There was an error loading the feed
                    </h3>
                    <div
                        class="mt-2 text-sm text-yellow-700 dark:text-yellow-200"
                    >
                        <p>
                            {err.message}
                        </p>
                    </div>
                </div>
            </div>
        </div>
    {/await}
</section>

<section id="goals">
    <h3 class="dark:text-gray-200 text-xl ml-4 pl-1 mb-2  ">Goals</h3>

    {#await getFeatures()}
        <Feature />
    {:then val}
        <Feature goals={val} />
    {:catch err}
        <!-- This example requires Tailwind CSS v2.0+ -->
        <div class="rounded-md bg-yellow-50 dark:bg-yellow-700 p-4">
            <div class="flex">
                <div class="flex-shrink-0">
                    <!-- Heroicon name: solid/exclamation -->
                    <svg
                        class="h-5 w-5 text-yellow-400"
                        xmlns="http://www.w3.org/2000/svg"
                        viewBox="0 0 20 20"
                        fill="currentColor"
                        aria-hidden="true"
                    >
                        <path
                            fill-rule="evenodd"
                            d="M8.257 3.099c.765-1.36 2.722-1.36 3.486 0l5.58 9.92c.75 1.334-.213 2.98-1.742 2.98H4.42c-1.53 0-2.493-1.646-1.743-2.98l5.58-9.92zM11 13a1 1 0 11-2 0 1 1 0 012 0zm-1-8a1 1 0 00-1 1v3a1 1 0 002 0V6a1 1 0 00-1-1z"
                            clip-rule="evenodd"
                        />
                    </svg>
                </div>
                <div class="ml-3">
                    <h3
                        class="text-sm font-medium text-yellow-800 dark:text-yellow-100"
                    >
                        There was an error loading the Features
                    </h3>
                    <div
                        class="mt-2 text-sm text-yellow-700 dark:text-yellow-200"
                    >
                        <p>
                            {err.message}
                        </p>
                    </div>
                </div>
            </div>
        </div>
    {/await}
</section>
