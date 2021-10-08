<template>
  <div>
    <h1 class="myClass">{{ title }}</h1>
    <div>
      <p>{{ content }}</p>
      <p>{{ author }}</p>
    </div>
    <button @click="callParent">Call Parent</button>
    <slot :insideComponent="insideComponent"></slot>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    content: String,
    author: {
      type:String,
      required: false,
      default: "Autor desconocido"
    },
  },

  data() {
    return {
      insideComponent: "Alhoo polizhia"
    };
  },
  methods: {
    callParent: function() {
      this.$emit("call-parent", this.author)
    }
  }
};
</script>

<style>
.myClass {
  font-size: 3em;
  color: blue !important;
}
</style>