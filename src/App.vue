<template>
  <div id="app">
    <v-header @change="change" />
    <div class="content">
      <v-form />
      <v-list />
    </div>
  </div>
</template>

<script>
import VHeader from "@/components/VHeader";
import VForm from "@/components/VForm";
import VList from "@/components/VList";

export default {
  name: "App",
  components: { VList, VForm, VHeader },
  methods: {
    change(value) {
      console.log(value);
    },
  },
};
</script>

<style lang="scss" scoped>
#app {
  background: rgba(255, 254, 251, 0.8);
  padding: 32px;
  max-width: 1440px;
  margin: 0 auto;
}
.content {
  display: flex;
  align-items: flex-start;
  gap: 26px;
  .form {
    flex: 0 0 322px;
  }
}
</style>
