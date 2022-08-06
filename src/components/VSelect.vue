<template>
  <select class="select" @change="change">
    <option selected disabled>По умолчанию</option>
    <option value="1">По цене min</option>
    <option value="2">По цене max</option>
    <option value="3">По наименованию</option>
  </select>
</template>

<script>
export default {
  name: "VSelect",
  methods: {
    change({ target }) {
      this.$emit("change", target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
.select {
  display: inline-flex;
  background: #fffefb;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  height: 36px;
  justify-content: center;
  align-items: center;
  padding: 0 27px 0 16px;
  font-size: 12px;
  line-height: 1.25;
  color: #b4b4b4;
  background: url("../assets/icons/chevron.svg") no-repeat;
  background-position-x: calc(100% - 16px);
  background-position-y: center;
  cursor: pointer;
  appearance: none;
}
</style>
