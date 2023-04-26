<script>
    export let 
        name = "",
        imgUrl = "",
        imgAlt = "",
        componentPage = "";
</script>

<div class="max-w-xl mx-auto rounded overflow-hidden shadow-lg p-4 w-full">
    <img class="w-full" src="{imgUrl}" alt="{imgAlt}">
    <div class="px-6 py-4">
        <div class="font-bold text-2xl mb-2">{name}</div>
        <p class="text-gray-700 text-base">
            <slot />
        </p>
    </div>
    <div class="px-6 pt-4 pb-2">
        <a href={componentPage} class="flex items-center justify-center h-12 px-5 text-sm font-medium text-center text-white transition-colors duration-300 transform rounded-lg xl:h-10 bg-purple-800 hover:bg-purple-800/70">Learn More</a>
    </div>
</div>