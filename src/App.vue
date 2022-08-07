<template>
  <div id="app">
    <v-header @change="change" />
    <div class="content">
      <v-form @submit="submit" />
      <v-list :list="sortedList" @remove="removeItem" v-if="list.length" />
      <div class="content__empty" v-else>- Товаров нет -</div>
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
  data() {
    return {
      list: [
        {
          id: 1,
          photo: require("@/assets/img/photo.jpg"),
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10000",
        },
        {
          id: 2,
          photo: require("@/assets/img/photo.jpg"),
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10000",
        },
        {
          id: 3,
          photo: require("@/assets/img/photo.jpg"),
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10000",
        },
        {
          id: 4,
          photo: require("@/assets/img/photo.jpg"),
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10000",
        },
        {
          id: 5,
          photo: require("@/assets/img/photo.jpg"),
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10000",
        },
        {
          id: 6,
          photo: require("@/assets/img/photo.jpg"),
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10000",
        },
        {
          id: 7,
          photo: require("@/assets/img/photo.jpg"),
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10000",
        },
        {
          id: 8,
          photo: require("@/assets/img/photo.jpg"),
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10000",
        },
        {
          id: 9,
          photo: require("@/assets/img/photo.jpg"),
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10000",
        },
      ],
      sortingNumber: 0,
    };
  },
  methods: {
    change(value) {
      this.sortingNumber = value;
    },
    removeItem(item) {
      this.list = this.list.filter((i) => i.id != item.id);
    },
    submit(item) {
      this.list = [...this.list, item];
    },
  },
  computed: {
    sortedList() {
      return [...this.list].sort((a, b) => {
        if (this.sortingNumber == 3) {
          return a.title.localeCompare(b.title);
        } else if (this.sortingNumber == 2) {
          return +a.price > +b.price ? -1 : 1;
        } else if (this.sortingNumber == 1) {
          return +a.price > +b.price ? 1 : -1;
        } else if (this.sortingNumber === 0) {
          return a;
        }
      });
    },
  },
  created() {
    if (localStorage.getItem("idaprojectList")) {
      this.list = JSON.parse(localStorage.getItem("idaprojectList"));
    }
  },
  watch: {
    list() {
      localStorage.setItem("idaprojectList", JSON.stringify(this.list));
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
    position: sticky;
    top: 24px;
    flex: 0 0 322px;
    @media (max-width: 1024px) {
      flex: 0 0 250px;
    }
  }
  &__empty {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 442px;
  }
  @media (max-width: 768px) {
    flex-wrap: wrap;
    gap: 24px;
    .form {
      flex: 0 0 100%;
      position: static;
    }
  }
}
</style>
