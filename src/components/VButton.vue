<template>
  <button @click="click" class="button">{{ text }}</button>
</template>

<script>
export default {
  name: "VButton",
  props: {
    text: {
      type: String,
      required: true,
    },
  },
  methods: {
    click() {
      this.$emit("click");
    },
  },
};
</script>

<style lang="scss" scoped>
.button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  height: 36px;
  width: 100%;
  padding: 0 10px;
  background: #7bae73;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  font-family: "Inter";
  font-weight: 600;
  font-size: 12px;
  line-height: 1.25;
  color: #fff;
  transition: background 0.3s, color 0.3s;
  &:disabled {
    background: #eee;
    color: #b4b4b4;
    pointer-events: none;
  }
}
@media (min-width: 1025px) {
  .button:hover {
    background: #aedba7;
  }
}
</style>
