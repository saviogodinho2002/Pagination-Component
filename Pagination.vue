<script setup lang="ts">

import {Link} from "@inertiajs/vue3";
import {ref, toRefs} from "vue";

const props = defineProps({
    links:Array
})
const {links} = toRefs(props)

const first = ref(links?.value?.shift())
const last = ref(links?.value?.pop())


function activeCss(value) {
    return !value?
        "flex items-center justify-center px-3 h-8 leading-tight text-gray-500 bg-white border border-gray-300 hover:bg-gray-100 hover:text-gray-700 dark:bg-gray-800 dark:border-gray-700 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-white"
        :"flex items-center justify-center px-3 h-8 text-blue-600 border border-gray-300 bg-blue-50 hover:bg-blue-100 hover:text-blue-700 dark:border-gray-700 dark:bg-gray-700 dark:text-white"
}

</script>

<template>
    <div class="text-center mt-5">

        <nav aria-label="Page navigation example">
            <ul class="inline-flex -space-x-px text-sm">
                <li>
                    <Link :href="first.url ?? '#'" class="flex items-center justify-center px-3 h-8 ml-0 leading-tight text-gray-500 bg-white border border-gray-300 rounded-l-lg hover:bg-gray-100 hover:text-gray-700 dark:bg-gray-800 dark:border-gray-700 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-white">Anterior</Link>
                </li>

                <li v-for="link in links">
                    <Link :href="link.url"
                          :class="activeCss(link.active)"

                              >
                        {{link.label}}
                    </Link>
                </li>
                <li>
                    <Link :href="last.url ?? '#'" class="flex items-center justify-center px-3 h-8 leading-tight text-gray-500 bg-white border border-gray-300 rounded-r-lg hover:bg-gray-100 hover:text-gray-700 dark:bg-gray-800 dark:border-gray-700 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-white">Próximo</Link>

                </li>
            </ul>
        </nav>
    </div>
</template>

<style scoped>

</style>