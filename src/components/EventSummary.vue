<script setup lang="ts">
defineProps<{
    description: string
    poster: string
    video: string
    slides: string
    notebook: string
    name: string
    bio: string
    website: string
    twitter: string
    linkedin: string
    github: string
    hide_personal_info: boolean
    lista: string
}>()
</script>

<template>
    <p class="contents" :description="description">{{ description }}</p>

    <div v-if="video" class="contents">
        <iframe class="mx-auto my-8" width="560" height="315" :src="video" title="YouTube video player" frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media;
            gyroscope; picture-in-picture" allowfullscreen></iframe>
    </div>
    <div v-else="poster" class="flex justify-center">
        <img alt="Cartel Evento" :src="poster" />
    </div>

    <div class="grid grid-cols-2">
        <div>
            <p v-if="!hide_personal_info" class="contents" :name="name">{{ name }}</p>
            <div v-if="!hide_personal_info" class="mt-2 flex flex-wrap gap-2 items-center justify-self-center" text="lg">
                <IconButtonLink v-if="website" :url="website" target="_blank" class="contents">
                    <carbon:user-avatar-filled-alt />
                </IconButtonLink>
                <IconButtonLink v-if="twitter" :url="twitter" target="_blank" class="contents">
                    <carbon:logo-twitter />
                </IconButtonLink>
                <IconButtonLink v-if="linkedin" :url="linkedin" target="_blank" class="contents">
                    <carbon:logo-linkedin />
                </IconButtonLink>
                <IconButtonLink v-if="github" :url="github" target="_blank" class="contents">
                    <carbon:logo-github />
                </IconButtonLink>
            </div>
        </div>
        <div>
            <div v-if="slides" class="flex justify-end">
                <a class="contents" :href="slides" target="_blank" rel="noreferrer">Diapositivas</a>
            </div>
            <div v-if="notebook" class="flex justify-end">
                <a class="contents" :href="notebook" target="_blank" rel="noreferrer">Notebook</a>
            </div>
        </div>
    </div>
    <div v-if="!hide_personal_info" class="my-8">{{ bio }}</div>
    <div v-if="lista" class="flex justify-center">
        <a :href="lista" target="_blank">Más charlas y talleres</a>
    </div>
</template>