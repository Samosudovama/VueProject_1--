

<template>
  
  <div className="center"> 
    <input type="text" v-model="userName" placeholder="Имя" className="userInput">
    <br>
    <input type="email" v-model="userEmail" placeholder="Email" className="userInput">
    <br>
    <input type="password" v-model="userPass" placeholder="Пароль" className="userInput">
    <br>
    <p className="error">{{ error }}</p>
    <button @click="sendData()"> <b>Отправить</b></button>    

    <div v-if="users.length == 0" className="userInput">
       У нас нет пользоваелей.
    </div>

    <div v-else-if="users.length == 1" className="userInput">
      У нас пока только один пользователь:      
    </div>    

    <div v-else className="userInput">
      Наши пользователи:
    </div>
  
    <div v-for="(el, index) in users" :key="index" className="userInput">
      <h1>{{ el.name }}</h1>
      <p>{{ el.email }} - <b>{{ el.pass }}</b></p> 
    </div> 

    <!-- <p>Вывод всего массива: {{ users }}</p> -->
  </div>

</template>

<script>
export default {
  data() {
    return {
      users: [],
      error: "",
      userName: "",
      userEmail: "",
      userPass: ""
    }
  },
  methods: {
    
    sendData() {
      if (this.userName == ''){
        this.error = 'Имя не введено';
         return;
        }else if(this.userEmail == ''){
          this.error = 'Email не введен';
          return;
        }else if(this.userPass == ''){
          this.error = 'Пароль не введен';
          return;
        }
        this.error = '';
     
      this.users.push({
        name: this.userName,
        email: this.userEmail,
        pass: this.userPass,
      })
    },
  }
}

</script>

<style scoped>

.userInput {
    width: 100%;
    padding: 2vh;
    background-color:aliceblue;
    border: solid 1px aliceblue;
    border-radius: 5px;
    margin-top: 20px;
    color: black;
  }
  
  .userInput:hover {
    border: solid 1px rgb(1, 137, 137); 
  }
  
  .user {
    min-width: 100%;
    margin-top: 20px;
    background-color: rgb(224, 229, 230);
    padding: 2vh;
    border:  0px;
    border-radius: 5px;;
  }
  
  button {
    width: 100%;
    margin-top: 20px;
    background-color: aliceblue;
    padding: 2vh;
    border: solid 2px aliceblue;
    border-radius: 5px;;
  }
  
  button:hover {
    border: solid 2px aliceblue;    
    background-color:  aqua;
  }
  
  @media (min-width: 1000px) {
  button:hover {       
    background-color:  rgb(175, 242, 242);
  }
}
</style>
