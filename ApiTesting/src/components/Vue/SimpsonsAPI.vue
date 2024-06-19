<script setup>

    import { ref } from 'vue'

    let chars = await fetch('https://thesimpsonsquoteapi.glitch.me/quotes?count=10')
    .then(response => response.json())
    .then(function(dataReceived) {
        return dataReceived
    })

    // console.log(await chars)

</script>

<template>
    <section class="max-w-3xl mx-auto my-20 flex justify-center items-center flex-col">
        <div v-for="(charInfo) in chars" 
        class="my-2 flex justify-center items-center
        rounded-lg bg-white w-[32rem] h-52 border border-yellow-600"
        
        :class="{'flex-row-reverse':charInfo.characterDirection=='Right'}">
            
            <div class="flex justify-center items-center size-40">
                <img :src="charInfo.image" alt="" class="h-32 w-24">
            </div>
                
            <section class="h-40 w-80 px-3 py-2 bg-white flex flex-col gap-2" :class="{'items-end':charInfo.characterDirection=='Right'}, {'text-right':charInfo.characterDirection=='Right'}">
                <h1 class="text-lg font-semibold">
                    {{charInfo.character}}
                </h1>
                <h2 class="text-sm">{{ charInfo.quote }}</h2>
            </section>
        </div>
    </section>
</template>