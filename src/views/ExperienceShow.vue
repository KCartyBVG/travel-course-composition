<template>
     <section>
        <h1>{{ experience.name }}</h1>
        <img :src="`/images/${experience.image}`" :alt="experience.name">
        <p>{{ experience.description }}</p>
    </section>
</template>

<script setup>
    import sourceData from '@/data.json'
    import {computed} from 'vue'

        const props = defineProps({
            id: {type: Number, required: true, },
            experienceSlug: {type: String, required: true,}
        })

        const destination = computed(() =>{
            const dest =  sourceData.destinations.find(
                destination => destination.id === props.id
            )
            return dest
        })
        
        const experience = computed(() => {
            console.log(destination)
           if (destination !== undefined){
            return destination.value.experiences.find(
                experience => experience.slug === props.experienceSlug
            )
           }
        })
        
    
        
</script>