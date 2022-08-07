<template>
  <div class="list">
    <v-item
      @remove="remove(item)"
      v-for="item in list"
      :key="item.id"
      :item="item"
    />
  </div>
</template>

<script>
import VItem from "@/components/VItem";

export default {
  name: "VList",
  components: { VItem },
  props: {
    list: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    remove(item) {
      this.$emit("remove", item);
    },
  },
};
</script>

<style lang="scss" scoped>
.list {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  flex: 1 1 auto;
}

.item {
  flex: 1 1 30%;
  max-width: 332px;
}
</style>
