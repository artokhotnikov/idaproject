<template>
  <div class="items">
    <transition-group name="slide-fade" tag="div" class="items__list">
      <v-item
        @remove="remove(item)"
        v-for="item in list"
        :key="item.id"
        :item="item"
      />
    </transition-group>
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
.items {
  flex: 1 1 auto;
  &__list {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 16px;
    @media (max-width: 1024px) {
      grid-template-columns: repeat(2, 1fr);
    }
    @media (max-width: 540px) {
      grid-template-columns: repeat(1, 1fr);
    }
  }
}

.slide-fade-enter-active {
  transition: all 0.5s ease;
}

.slide-fade-leave-active {
  transition: all 0.6s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter,
.slide-fade-leave-to {
  transform: translateX(10px);
  opacity: 0;
}
.slide-fade-move {
  transition: transform 0.5s ease;
}
</style>
