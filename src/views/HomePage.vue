<template>
  <div class="containe mx-auto">
    <!--  <h1 class="font-bold text-xxl text-green-300">{{ message }}</h1>-->

    <!--  <ul>-->
    <!--    <number></number>-->
    <!--&lt;!&ndash;    <number />&ndash;&gt;-->
    <!--&lt;!&ndash;    <Number></Number>&ndash;&gt;-->
    <!--&lt;!&ndash;    <Number />&ndash;&gt;-->
    <!--&lt;!&ndash;    <abc></abc>&ndash;&gt;-->
    <!--    <school-name/>-->
    <!--  </ul>-->

    <!--  <SlotComponent>-->
    <!--    <h2>My name is Emran</h2>-->
    <!--  </SlotComponent>-->
    <button
      @click="addPost"
      class="px-1 border border-blue-400 rounded-md bg-blue-100 mb-4 mt-2"
    >
      Add post
    </button>
    <br />
    <!--  {{name}}-->
    <!--  Fav Count : {{ favCount }} <br>-->
    <!--  Un Fav Count : {{ unFavCount}}-->
    <h1>All Post ({{ posts.length }})</h1>
    <hr class="mb-4" />
    <ul>
      <single-post
        v-for="(post, index) in posts"
        :key="index"
        :post="post"
        @delete="handleDelete($event)"
        @fav="handleFav"
      />

      <!--      v-for="post in posts"-->
      <!--      :key="post.id"-->
      <!--      @delete="handleDelete($event, true)"-->
    </ul>
    <br />
    <h1>Fav Post ({{ favCount }})</h1>
    <hr class="mb-4" />
    <ul>
      <single-post
        v-for="(post, index) in favs"
        :key="index"
        :post="post"
        @delete="handleDelete($event)"
        @fav="handleFav"
      />
    </ul>
    <br />
    <h1>Un Fav Post ({{ unFavCount }})</h1>
    <hr class="mb-4" />
    <ul>
      <single-post
        v-for="(post, index) in unFavs"
        :key="index"
        :post="post"
        @delete="handleDelete($event)"
        @fav="handleFav"
      />
    </ul>
  </div>
</template>

<script>
import Number from "../components/Number.vue";
import SchoolName from "../components/SchoolName.vue";
import SlotComponent from "../components/SlotComponent.vue";
import SinglePost from "../components/SinglePost.vue";
export default {
  name: "HomePage",
  components: { SinglePost, SlotComponent, SchoolName, Number },
  // components: {abc: Number},
  data() {
    return {
      idCount: 3,
      message: "Hello Bangladesh",
      posts: [
        {
          id: 1,
          title: "post 1",
          fav: true,
        },
        {
          id: 2,
          title: "post 2",
          fav: false,
        },
        {
          id: 3,
          title: "post 3",
          fav: true,
        },
      ],
      // first_name: 'Raihanul Haq',
      // last_name: 'Emran'
      // string: "Hello World",
      // object: {},
      // array: [],
      // boolean: true,
      // number: 1
    };
  },
  computed: {
    // name() {
    //   return `${this.first_name} ${this.last_name}`
    // }
    favCount() {
      return this.posts.filter((post) => post.fav).length;
    },
    favs() {
      return this.posts.filter((post) => post.fav);
    },
    unFavCount() {
      return this.posts.filter((post) => !post.fav).length;
    },
    unFavs() {
      return this.posts.filter((post) => !post.fav);
    },
  },
  methods: {
    handleDelete(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    addPost() {
      this.idCount = this.idCount + 1;
      // console.log(this.idCount);
      // console.log(this.posts.length);
      // this.posts.unshift({
      this.posts.push({
        // id:this.posts.length+1,
        id: Math.floor(Math.random() * 10000),
        // title: "post "+(this.posts.length+1)
        title: "post " + this.idCount,
      });
    },
    handleFav(post) {
      this.posts = this.posts.map((p) => {
        if (p.id === post.id) {
          p.fav = !p.fav;
        }
        return p;
      });
    },
  },

  // beforeCreate() {
  //   console.log("HomePage before create")
  // },
  // created() {
  //   console.log("HomePage created")
  // },
  // beforeMount() {
  //   console.log("Homepage Before Mount")
  // },
  // mounted() {
  //   console.log("HomePage mounted")
  // },
  // beforeUnmount() {
  //   console.log("HomePage beforeUnmount")
  // },
  // unmounted() {  console.log("HomePage unmounted")
  // }
};
</script>

<style scoped></style>
