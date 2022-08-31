<template>
    <div class="form_container" @keyup.esc="$emit('close-window')">
        <form @submit.prevent="$emit('form-submit', name, email)" class="reg_form" @keyup.esc="$emit('close-window')">
            <h1>Заявка на участие</h1>
            <div class="input_container">
                <input v-model="name" class="FIO_input" type="text " placeholder="ФИО" required>
                <input v-model="email" class="email_input" type="email" placeholder="E-mail" required> 
            </div>
            <button type="submit">Отправить</button>
        </form>
    </div>
</template>

<script>
export default {
  data () {
    return {
        name: "",
        email: ""
    }
  },
}
</script> 

<style scoped>
    .form_container {
        position: absolute;
        z-index: 20;
        top: 0; left: 0; bottom: 0; right: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(255,255, 255, 0.5);
    }

    .reg_form {
        border: 0;
        border-radius: 20px;
        width: 740px;
        height: 500px;
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
        align-items: center;
        box-shadow: 2px 2px 6px rgba(0, 0, 0, 0.3);
        background-color: white;
        margin: 25px auto auto auto;
    }

    input {
        padding-left: 15px;
        font-size: 20px;
        border: 1px solid #C3C3C3;
        border-radius: 15px;
        width: 540px;
        height: 54px;
    }

    .input_container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .FIO_input {
        margin-bottom: 40px;
    }

    button {
        background-color: #6C8474;
        color: #F3F3F3;
        font-size: 20px;
        width: 227px;
        height: 58px;
        border: 0;
        transition: .1s;
        border-radius: 29px;
    }

    button:hover {
        background-color: #bbbbbb;
        color: #777777;

    }

    h1 {
        font-size: 28px;
    }
</style>