<template>
    <div v-if="show" class="popup">
        <div class="popup-content">
            <h2>Форма</h2>
            <form @submit.prevent="submitForm">
                <label for="name">Имя:</label>
                <input type="text" id="name" v-model="formData.name">
                <span  class="error-message">Обязательное поле</span>

                <label for="phone">Телефон:</label>
                <input type="text" id="phone" v-model="formData.phone" @input="formatPhone">
                <span class="error-message">Обязательное поле</span>

                <label for="email">Email:</label>
                <input type="email" id="email" v-model="formData.email">
                <span class="error-message">Обязательное поле</span>

                <label for="city">Город:</label>
            <select id="city" v-model="formData.city" required>
                <option value="">Выберите город</option>
                <option value="Москва">Москва</option>
                <option value="Санкт-Петербург">Санкт-Петербург</option>
            </select>
        <button type="submit" @click.prevent="submitForm">Отправить</button>
        </form>
            <button @click="closePopup">Закрыть</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TaskPopupForm',

    props: ['show', 'button'],

    data() {
        return {
            formData: {
                name: '',
                phone: '',
                email: '',
                city: '',
                // isEmailValid: false,
                // isPhoneValid: false
            }
        };
    },

    mounted() {
        
    },

    methods: {
        openForm() {
            this.isFormVisible = true;
        },
        closePopup() {
            this.$emit('close');
        },
    }
};
</script>

<style lang="scss" scoped>
.popup {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;

  &-content {
    background-color: #fff;
    padding: 20px calc(var(--index) * 5);
    border: 3px solid transparent;
    border-image: linear-gradient(to right, rgba(209, 23, 23, 0.85), rgba(208, 230, 10, 0.8)) 1;
    background-color: rgba(218, 209, 209, 0.873);
  }

  &-content form {
    display: flex;
    flex-direction: column;
  }

  &-content label {
    margin-bottom: 10px;
  }

  &-content input, &-content select {
    margin-bottom: 10px;
  }

  &-content button {
    margin-bottom: 10px;
  }
}
</style>