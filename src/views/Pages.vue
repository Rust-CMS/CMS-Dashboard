<template>
    <main>
        <h1>Pages</h1>
        <PageTable :pages="pages" />
    </main>
</template>

<script>
import { get } from "axios";

import PageTable from '@/components/PageTable';

export default {
    name: "Pages",
    data() {
        return {
            pages: []
        }
    },
    components: {
        PageTable
    },
    async created() {
        let pages = await this.get_pages();
        this.pages = pages.message;
    },
    methods: {
        async get_pages() {
            let pages_req = await get("/pages");
            return pages_req.data;
        }
    }
}
</script>