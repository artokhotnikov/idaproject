<template>
  <div class="item">
    <div class="item__delete" @click="remove"></div>
    <div class="item__img">
      <img src="../assets/img/photo.jpg" alt="Фотография" />
    </div>
    <div class="item__body">
      <div class="item__title">Наименование товара</div>
      <div class="item__description">
        Довольно-таки интересное описание товара в несколько строк.
        Довольно-таки интересное описание товара в несколько строк
      </div>
      <div class="item__price">10 000 руб.</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "VItem",
  methods: {
    remove() {
      this.$emit("remove");
    },
  },
};
</script>

<style lang="scss" scoped>
.item {
  position: relative;
  display: flex;
  flex-direction: column;
  background: #fffefb;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  cursor: pointer;

  &__delete {
    width: 34px;
    height: 37px;
    position: absolute;
    z-index: 2;
    top: -9px;
    right: -9px;
    background: url("../assets/icons/delete.svg") center / auto no-repeat;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.3s;
  }

  &__img {
    overflow: hidden;
    position: relative;
    padding-top: 60%;
    border-radius: 4px 4px 0 0;

    img {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

  &__body {
    padding: 16px 16px 24px;
    display: flex;
    flex-direction: column;
    height: 100%;
  }

  &__title {
    font-weight: 600;
    font-size: 20px;
    line-height: 1.25;
    margin-bottom: 16px;
  }

  &__description {
    line-height: 1.25;
    margin-bottom: 32px;
  }

  &__price {
    font-weight: 600;
    font-size: 24px;
    line-height: 1.25;
    margin-top: auto;
  }
  @media (min-width: 1025px) {
    &:hover &__delete {
      opacity: 1;
      pointer-events: all;
    }
  }
}
</style>
