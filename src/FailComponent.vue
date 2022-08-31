<template>
    <div class="success_window">
        <img src="../public/img/fail.png">
        <div class="success-text"><p>К сожалению,<wbr> нам не удалось отправить данные</p></div>
    </div>
</template>

<style scoped>
    .success_window {
        position: absolute;
        z-index: 30;
        display: flex;
        justify-content: space-evenly;
        flex-direction: column;
        background-color: white;
        width: 380px;
        height: 320px;
        border: 0;
        border-radius: 20px;
        align-items: center;
        top: 0; left: 0; bottom: 0; right: 0;
        margin: auto;
        box-shadow: 2px 2px 6px rgba(0, 0, 0, 0.2);
    }

    img {
        width: 120px;
        height: 120px;
    }

    p {
        margin: 0;
        padding: 0;
        font-size: 30px;
        line-height: normal;
        text-align: center;
        color: #444444;
    }

    .success-text {
        width: 100%;
        height: 120px;
    }
</style>