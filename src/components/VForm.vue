<template>
  <form class="form" @submit.prevent="submit">
    <v-input
      placeholder="Наименование товара"
      label="Наименование товара"
      id="name"
      :is-required="true"
      v-model.trim="item.title"
    />
    <v-input
      type="textarea"
      placeholder="Введите описание товара"
      label="Описание товара"
      id="about"
      :is-required="false"
      v-model.trim="item.description"
    />
    <v-input
      placeholder="Ссылка на изображение товара"
      label="Введите ссылку"
      id="img"
      :is-required="true"
      v-model.trim="item.photo"
    />
    <v-input
      placeholder="Введите цену"
      label="Цена товара"
      id="price"
      :is-required="true"
      v-model.trim="item.price"
    />
    <v-button :disabled="emptyForm" text="Добавить товар" />
  </form>
</template>

<script>
import VInput from "@/components/VInput";
import VButton from "@/components/VButton";

export default {
  name: "VForm",
  components: { VButton, VInput },
  data() {
    return {
      item: {
        id: "",
        photo: "",
        title: "",
        description: "",
        price: "",
      },
    };
  },
  methods: {
    submit() {
      this.item.id = Date.now();
      this.$emit("submit", this.item);
      this.item = {};
    },
  },
  computed: {
    emptyForm() {
      return !(this.item.title && this.item.photo && this.item.price);
    },
  },
};
</script>

<style lang="scss" scoped>
.form {
  position: sticky;
  top: 24px;
  padding: 24px;
  background: #fffefb;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
}
.form-control + .form-control {
  margin-top: 16px;
}
.button {
  margin-top: 24px;
}
</style>
