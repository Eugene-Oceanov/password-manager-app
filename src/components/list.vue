<template>
    
    <div class="list">
        <list-item v-for="item in itemsArr" :key="item.id" :listItem="item" />
    </div>
</template>

<script>
import listItem from "@/components/list-item.vue";

export default {
    components: {
        listItem
    },
    props: {
        itemsArr: {
            type: Array,
            required: true
        }
    }
}

</script>