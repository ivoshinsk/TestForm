<template>
    <div>
        <div class="btn">
            <button class="btn-form" @click="openPopup">Заказать в Москву</button>
            <button class="btn-form" @click="openPopup">Заказать в Санкт-Петербург</button>
        </div>
        <PopupForm :show="showPopup" @close="closePopup" :button="activeButton"/>
    </div>
</template>

<script>
import PopupForm from './PopupForm.vue';

export default {
    name: 'TaskButtonCity',
    components: {
        PopupForm,
    },

    data() {
        return {
            showPopup: false,
            activeButton: ''
        };
    },

    mounted() {
        
    },

    methods: {
        openPopup(button) {
            this.showPopup = true;
            this.activeButton = button;
        },
        closePopup() {
            this.showPopup = false;
            this.activeButton = '';
        },
            submitForm() {
        if (this.name && this.email && this.phone && this.isEmailValid && this.isPhoneValid) {
            alert('Форма отправлена!');
            this.isFormVisible = false;
        } else {
            alert('Пожалуйста, заполните все поля правильно.');
        }
    },
    formatPhone() {
        let formattedPhone = this.phone.replace(/\D/g, '');
        if (formattedPhone.length === 11) {
            this.phone = '+7 (' + formattedPhone.substring(1, 4) + ') ' + formattedPhone.substring(4, 7) + '-' + formattedPhone.substring(7, 9) + '-' + formattedPhone.substring(9);
            this.isPhoneValid = true;
        } else {
            this.isPhoneValid = false;
        }
    },
    },
    watch: {
        email(value) {
            this.isEmailValid = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value);
        }
    },
};
</script>

<style lang="scss" scoped>
.btn {
    display: flex;
    justify-content: space-around;
    align-items: center;

    .form {
        display: flex;
        justify-content: space-between;
    }

    button {
        background: rgba(209, 23, 23, 0.75);
        font-family: inherit;
        padding: 0.6em 1.3em;
        margin-right: 10px;
        font-weight: 900;
        font-size: 18px;
        border: 3px solid black;
        border-radius: 0.4em;
        box-shadow: 0.1em 0.1em;
        cursor: pointer;

        &:hover {
            transform: translate(-0.05em, -0.05em);
            box-shadow: 0.15em 0.15em;
        }

        &:active {
            transform: translate(0.05em, 0.05em);
            box-shadow: 0.05em 0.05em;
        }
    }
}
</style>



