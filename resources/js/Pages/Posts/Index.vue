<template>
    <app-layout>
        <div v-if="$page.props.flash.success" class="bg-green-600 text-white">
            {{ $page.props.flash.success }}
        </div>
        <div>
            <inertia-link class="border bg-indigo-300 rounded-xl px-4 py-2 m-4" :href="route('posts.create')">
                <span>Create</span>
            </inertia-link>        
        </div>
        <div class="">
            <table class="shadow-lg border m-4 rounded-xl">
                <thead>
                    <tr class="bg-indigo-100">
                        <th class="py-2 px-4 border">Title</th>
                        <th class="py-2 px-4 border">Body</th>
                        <th class="py-2 px-4 border">Actions</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="item in data" :key="item.id">
                        <td class="py-2 px-4 border">{{item.title}}</td>
                        <td class="py-2 px-4 border">{{item.body}}</td>
                        <td class="py-2 px-4 border">
                            <inertia-link class="border bg-indigo-300 rounded-xl px-4 py-2 m-4" :href="route('posts.edit', item.id)">
                                <span>Edit</span>
                            </inertia-link>        
                            <button class="border bg-indigo-300 rounded-xl px-4 py-2 m-4" @click="destroy(item.id)">
                                <span>Delete</span>
                            </button>        
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </app-layout>
</template>

<script>
    import AppLayout from '@/Layouts/AppLayout'

 export default {
        components: {
            AppLayout,
        },
        props: ['data'],
        data(){
            return {
                
            }
        },
        methods: {
        destroy(id) {
            this.$inertia.delete(this.route('posts.destroy', id))
            },        
        },
    }
</script>
