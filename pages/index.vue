<template>
<div class="flex h-screen justify-center items-center">
  <div class="bg-gray-100 p-8 shadow-lg">
    <div>
      <Logo />
      <div class="flex justify-center">
        <h1 class="text-gray-900 font-base m-4 text-xl">
          Test-app
        </h1>
      </div>
        <vs-alert>
            Includes
             <vs-checkbox v-model="option1">TailwindCSS</vs-checkbox>
             <vs-checkbox v-model="option2">Vuesax</vs-checkbox>
             <vs-checkbox v-model="option3">Axios</vs-checkbox>
        </vs-alert>
    </div>
  </div>
</div>
</template>

<script>
export default {
  data(){
    return{
      option1: true,
      option2: true,
      option3: true
    }
  },
  // Single Request
  // asyncData({$axios}) {
  //   return $axios.$get('https://jsonplaceholder.typicode.com/posts')
  //   .then(res => {
  //     return {posts: res}
  //   })
  // },

  // Multiple Requests
  async asyncData({$axios}) {
    let postsData = await $axios.$get('https://jsonplaceholder.typicode.com/posts')
    let todosData = await $axios.$get('https://jsonplaceholder.typicode.com/todos')
    return {posts: postsData, todos: todosData}
  },
}
</script>
