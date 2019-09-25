<template>
  <div class="page-article" v-if="model">
    <div class="d-flex py-3 px-2 border-bottom">
      <router-link tag="div" to="/" class="iconfont icon-fanhui text-blue"></router-link>
      <strong class="flex-1 text-blue text-ellipsis pl-2">
        {{model.title}}
      </strong>
      <div class="text-grey fs-xs">
        2019-09-24
      </div>
    </div>
    <div v-html="model.body" class="img px-3 body fs-xl text-dark-1"></div>
    <div class="px-3 border-top py-3">
      <div class="d-flex ai-center">
        <i class="iconfont icon-Menu"></i>
        <strong class="text-blue fs-lg ml-1">相关资讯</strong>
      </div>
      <div class="pt-2">
        <router-link
                class="py-1"
                tag="div"
                :to="`/articles/${item._id}`"
                v-for="item in model.related"
                :key="item._id">
          {{item.title}}
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Article",
    props: {
      id: {
        required: true
      }
    },
    data() {
      return {
        model: null
      }
    },
    watch: {
      id: 'fetch'
      // id() {
      //   this.fetch()
      // }
    },
    methods: {
      async fetch() {
        const res = await this.$http.get(`articles/${this.id}`);
        this.model = res.data
      }
    },
    created() {
      this.fetch()
    }
  }
</script>

<style lang="scss" scoped>
    .page-article {
       .icon-fanhui {
         font-size: 1.385rem
       }

     }
</style>
