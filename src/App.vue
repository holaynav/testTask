<template>
  <div class="wrapper">
        <main class="container">
            <section class="about-us">
                <h1>Мастер-классы от Create Studio</h1>
                <button @click="isFormVisible = !isFormVisible" @keyup.esc="isFormVisible=false" type="submit" class="btn">Записаться</button>
            </section>
            <FormComponent v-if="isFormVisible" v-on:close-window="closeWindow" v-on:form-submit="formSubmit" />
            <SuccessComponent v-if="isFetchOk" />
            <FailComponent v-if="isFetchNotOk" />
        </main>
    </div>
</template>

<script>
import FormComponent from './FormComponent.vue';
import SuccessComponent from './SuccessComponent.vue';
import FailComponent from './FailComponent.vue';

export default {
  name: 'App',
  components: {
    FormComponent,
    SuccessComponent,
    FailComponent
},
  data () {
    return {
      isFormVisible : false,
      isFetchOk : false,
      isFetchNotOk : false,
      email: "",
      name: ""
    }
  },
  methods: {
    closeWindow() {
      this.isFormVisible = false;
    },
    formSubmit(name, email) {
      this.name = name;
      this.email = email;
      this.sendData();
    },
    async sendData () {
      try {
        const res = await fetch('https://jsonplaceholder.typicode.com/users', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        credentials: 'include',
        body: JSON.stringify({
          name: this.name,
          email: this.email
        })
      })
      this.closeWindow();
      this.isFetchOk = true;
      setTimeout(() => { this.isFetchOk = false} , 2000);
      console.log(res);
      } catch (error) {
        this.isFetchNotOk = true;
        setTimeout(() => { this.isFetchNotOk = false }, 2000);
      }
    }
  }
}
</script>

<style>
  body {
  margin: 0;
  padding: 0;

  font-size: 14px;
  line-height: 20px;
  font-family: "Roboto", "Verdana", sans-serif;
  color: #000000;
  background-color: #E3E5E1;

}

.wrapper {
  background: url(../public/img/bgimage.png) no-repeat 0 0;
}

.container {
  position: relative;
  width: 1300px;
  margin: 0 auto;
  padding: 0;
  background: url(../public/img/office.png) no-repeat 700px 120px;

}

.about-us {
  width: 500px;
  min-height: 400px;
  padding-left: 90px;
  padding-top: 150px;

}

.about-us h1 {
  margin: 0;
  margin-bottom: 80px;

  font-size: 65px;
  line-height: 65px;
  color: #6C8474;
}

.btn {
  position: relative;

  display: block;
  width: 330px;
  height: 80px;
  margin: 0;
  font-weight: 400;
  font-size: 26px;
  line-height: 30px;
  text-align: center;
  color: #F3F3F3;
  background-color: #6C8474;
  border: none;
  box-shadow: 0px 2px 3px rgba(0, 0, 0, 0.28);
  border-radius: 50px;
}

.btn:hover {
  background-color: white;
  color: #6C8474;
  border: none;
}

.btn:active {
  background-color: #D9D9D9;
}
</style>
