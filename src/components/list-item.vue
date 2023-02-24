<template>
    
<div class="list-item">
    <p class="list-item-date">{{ listItem.date }}</p>
    <a :href="listItem.link">{{ listItem.title }}</a>
    <p>Login: <span class="bold">{{ listItem.login }}</span></p>
    <p>Password: <span class="bold">{{ listItem.password }}</span></p>
    <hr>
</div>

</template>

<script>
export default {
    props: {
        listItem: {
            type: Object,
            required: true
        }
    }
}
</script>