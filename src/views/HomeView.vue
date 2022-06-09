<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error">{{error}}</div>
    <div v-if="posts.length">
        <PostList v-if="showPosts" :posts="posts"/>
    </div>
    <div v-else>Loading...</div>

    <button @click="showPosts = !showPosts">toggle posts</button>
    <button @click="posts.pop()">delete a post</button>
    <!-- <h2>Refs</h2> 
    <p>{{bb.name}} - {{bb.age}}</p>
    <button @click="updateBB">update BB</button>
    <hr/>
    <h2>Reactive</h2>
    <p>{{bb2.name}} - {{bb2.age}} - {{name2}}</p>
    <button @click="updateBB2">update BB2</button> -->

    <!-- <h2>Computed</h2>
    <input type="text" v-model="search">
    <p>search term - {{search}} </p>
    <div v-for="name in matchingNames" :key="name">{{name}}</div> -->

    <!--watch-->
    <!-- <button @click="handleClick">stop watching</button> -->

  </div>
</template>

<script>
import PostList from '../components/PostList.vue'
import {ref, computed, watch, watchEffect} from 'vue'
import getPosts from '../composables/getPosts'

export default {
  name: 'HomeView',
  components: {PostList},
  setup(){

    const{ posts, error, load } = getPosts()
    load()

    // -- ref vs reactive
    // const bb = ref({name: 'mario', age: 30})
    // const bb2 = reactive({name: 'luigi', age: 40})

    // const name1 = ref('mario')
    // const name2 = reactive('luigi')

    // const updateBB = () => {
    //   bb.value.age = 35
    // }

    // const updateBB2 = () => {
    //   bb2.age = 45
    // }

    // return { bb, updateBB , bb2, updateBB2, name2}


    //-- computed value
    // const search = ref('')
    // const names = ref(['mario', 'yoshi', 'luigi', 'toad', 'bowser', 'koopa', 'peach'])

    // const stopWatch = watch(search, () => {
    //   console.log('watch function')
    // })

    // const stopEffect = watchEffect(() => {
    //   console.log('watchEffect function ran', search.value)
    // })

    // const matchingNames = computed(() => {
    //   return names.value.filter((name) => name.includes(search.value))
    // })

    // const handleClick = () => {
    //   stopWatch()
    //   stopEffect()
    // }

    // return { names, search, matchingNames }

    //-- using props in setup
   

    const showPosts = ref(true)

    return {showPosts, posts, error}
  }
}
</script>
