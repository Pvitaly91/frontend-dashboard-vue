<template>
    <div class="flex justify-center items-center min-h-full w-full min-w-full">
        <div class="flex">
            <div class="text-indigo-600 self-start text-5xl border-r font-bold px-8 pb-8 leading-10">404</div>
            <div class="px-8">
                <h1 class="text-5xl font-bold  mb-2">Page Not Found</h1>
                <p class="text-gray-400 mb-10">Please check the url in address bar and try again</p>
                <div>
                    <router-link :to="{name:'app.dashboard'}" 
                    class=" rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">
                        Go back home
                    </router-link >
                </div>
            </div>
        </div>

    </div>
</template>

<script>

    export default {
        name: "NotFpund"
    }
</script>