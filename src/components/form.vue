<template>
    <form action="#" @submit.prevent="save">
        <div class="inputs-line">
            <input type="text" class="left-input" placeholder="*title" required v-model="title">
            <input type="text" class="right-input" placeholder="link" v-model="link">
        </div>
        <div class="inputs-line">
            <input type="text" class="left-input" placeholder="*login" required v-model="login">
            <input type="text" class="right-input" placeholder="*password" required v-model="password">
        </div>
        <div class="buttons-line">
            <input class="button" type="submit" value="Save">
            <input class="button" type="button" value="Password generator" @click="openGen">
        </div>
    </form>
</template>

<script>
    export default {
        data() {
            return {
                id: 0,
                title: "",
                link: "",
                login: "",
                password: "",
            }
        },
        methods: {
            save(){
                this.$emit("save", {
                    id: this.id,
                    title: this.title,
                    link: this.link,
                    login: this.login,
                    password: this.password,
                    date: new Date(Date.now()).toLocaleString(),
                })
                this.id++;
                this.title = "";
                this.link = "";
                this.login = "";
                this.password = "";
            },
            openGen(){
                this.$emit("openGen", true)
            }
        },
    }
</script>