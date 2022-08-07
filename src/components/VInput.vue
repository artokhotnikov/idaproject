<template>
  <div class="form-control" :class="{ error: isError, required: isRequired }">
    <label :for="id">{{ label }}</label>
    <input
      v-if="type === 'input'"
      :id="id"
      :name="id"
      :placeholder="placeholder"
      type="text"
      :value="value"
      @input="input"
    />
    <textarea
      v-if="type === 'textarea'"
      :placeholder="placeholder"
      :name="id"
      :id="id"
      :value="value"
      @input="input"
    ></textarea>
    <span v-if="isError" class="form-control__error">
      Поле является обязательным
    </span>
  </div>
</template>

<script>
export default {
  name: "VInput",
  data() {
    return {
      isError: false,
    };
  },
  props: {
    type: {
      type: String,
      default: "input",
      required: false,
    },
    placeholder: {
      type: String,
      required: true,
    },
    id: {
      type: String,
      required: true,
    },
    label: {
      type: String,
      required: true,
    },
    isRequired: {
      type: Boolean,
      required: true,
    },
    value: {
      type: String,
    },
  },
  methods: {
    input({ target }) {
      this.$emit("input", target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
.form-control {
  &.required {
    label:after {
      content: "";
      display: block;
      width: 4px;
      height: 4px;
      background: #ff8484;
      border-radius: 4px;
    }
  }

  &.error {
    input {
      border: 1px solid #ff8484;
    }
  }

  &__error {
    font-size: 8px;
    line-height: 1.25;
    letter-spacing: -0.02em;
    color: #ff8484;
    margin-top: 4px;
    display: block;
  }

  label {
    font-size: 10px;
    line-height: 1.3;
    letter-spacing: -0.02em;
    color: #49485e;
    display: flex;
    align-items: flex-start;
    margin-bottom: 4px;
  }

  input {
    background: #fffefb;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 4px;
    font-size: 12px;
    line-height: 1.25;
    display: flex;
    padding: 0 16px;
    height: 36px;
    width: 100%;
    border: 1px solid transparent;
    transition: border-color 0.3s;

    &::placeholder {
      color: #b4b4b4;
    }
  }

  textarea {
    resize: none;
    padding: 10px 16px;
    width: 100%;
    background: #fffefb;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 4px;
    height: 108px;
    font-size: 12px;
    line-height: 1.25;
    border: 1px solid transparent;
    transition: border-color 0.3s;
    &::placeholder {
      color: #b4b4b4;
    }
  }
}
@media (min-width: 1025px) {
  .form-control {
    input:hover,
    input:focus,
    textarea:hover,
    textarea:focus {
      border-color: #b4b4b4;
    }
  }
}
</style>
