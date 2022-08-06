<template>
  <header class="header">
    <h1 class="title">Добавление товара</h1>
    <v-select @change="change" />
  </header>
</template>

<script>
import VSelect from "@/components/VSelect";
export default {
  name: "VHeader",
  components: { VSelect },
  methods: {
    change(value) {
      this.$emit("change", value);
    },
  },
};
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 8px;
}

.title {
  font-weight: 600;
  font-size: 28px;
  line-height: 1.25;
}
</style>
