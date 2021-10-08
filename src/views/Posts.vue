<template>
  <div>
    <Post
      v-for="(post, index) in posts"
      :key="index"
      :title="post.title"
      :content="post.content"
      @call-parent="manageCall"
    >
      <div slot-scope="{ insideComponent }">Este es mi contenido desde fuera del componente {{insideComponent}}</div>
    </Post>
    <div>
      <button @click="goToHome">Al home</button>
    </div>
    <div>Del hijo: {{fromChild}}</div>
  </div>
</template>

<script>
import Post from "@/components/Post.vue";

export default {
  components: { Post },
  data() {
    return {
      posts: [
        {
          title: "Mi nuevo post",
          content: "Un post y muchas cosas más.",
          author: "YO",
        },
        {
          title: "Otro post",
          content: "pss otro",
          author: "el gil ",
        },
      ],
      fromChild: "hijito :3",
      counter: 0
    };
  },
  methods: {
    goToHome: function () {
      this.$router.push("/");
    },
    manageCall: function(author){
      this.fromChild="ya me llamaron a comer " + this.counter++ + author
    }
  },
};
</script>