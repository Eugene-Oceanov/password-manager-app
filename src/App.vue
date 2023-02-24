<template>

  <div class="generator-wrapper" v-show="generatorFlag" @click.self="generatorFlag = false">
    <generator />
  </div>
  <div class="manager">
    <h1>Vue password manager</h1>
    <forma @save="getPost" @openGen="openGen"/>
    <list :itemsArr="itemsArr"/>
  </div>
</template>

<script>
  import forma from "@/components/form.vue";
  import list from "@/components/list.vue";
  import generator from "@/components/generator.vue"
  export default {
    components: {
      forma,
      list,
      generator
    },
    data() {
      return {
        generatorFlag: true,
        itemsArr: [
          {
            id: 0,
            title: "Ingos",
            link: "https://www.ingos.ru",
            login: "Oceanov",
            password: "qwerty1234",
            date: new Date(Date.now()).toLocaleString(),
          }
        ]
      }
    },
    methods: {
      getPost(obj) {
        this.itemsArr.push(obj);
      },
      openGen(value) {
        this.generatorFlag = value;
      }
    }
  }
</script>