<template>
  <div id="app">
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css"
      rel="stylesheet"
      integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN"
      crossorigin="anonymous"
    />
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Work+Sans:wght@200;300;400;500;700&display=swap"
      rel="stylesheet"
    />
    <title>Crie sua conta na Memorar</title>

    <meta name="viewport" content="width=device-width, initial-scale=1" />

    <body>
      <div class="container my-4 col-lg-6 col-xl-4">
        <div class="d-flex justify-content-center">
          <img
            src="https://memorar.fot.br/images/company/memorar.fot.br.png"
            alt="Logo Loja Memorar"
            width="200px"
          />
        </div>
        <h1 class="text-center h5 fw-bold mt-2 mb-3">
          Crie sua conta na Memorar
        </h1>
        <form id="createAccount" class="row gx-3" @submit.prevent="onSubmit">
          <div class="form-floating mb-3">
            <input
              type="text"
              v-model="userForm.name"
              class="form-control"
              id="floatingName"
              placeholder="Nome Completo"
              required
            />
            <label for="floatingName">Nome Completo:</label>
          </div>
          <div class="col-sm-6 form-floating mb-3">
            <input
              type="tel"
              v-model="userForm.phone"
              class="form-control"
              id="floatingPhoneNumber"
              placeholder="Telefone"
              pattern="^\s*(\d{2})[-. ]?(\d{5}|\d{4})[-. ]?(\d{4})\s*$"
              required
            />
            <label for="floatingPhoneNumber">Telefone:</label>
          </div>
          <div class="col-sm-6 form-floating mb-3">
            <input
              type="date"
              v-model="userForm.birthDate"
              class="form-control"
              id="floatingBirth"
              placeholder="Data de Nascimento"
              required
            />
            <label for="floatingBirth">Data de Nascimento:</label>
          </div>
          <div class="form-floating mb-3">
            <input
              type="floatingMail"
              v-model="userForm.email"
              class="form-control"
              id="floatingMail"
              placeholder="floatingMail"
              pattern="^\w+([-+.']\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$"
              required
            />
            <label for="floatingMail">E-mail:</label>
          </div>
          <div class="col-sm-6 form-floating">
            <input
              type="floatingPassword"
              v-model="userForm.pass1"
              class="form-control"
              id="floatingPassword"
              placeholder="Senha"
              pattern="^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,}$"
              required
            />
            <label for="floatingPassword">Crie uma senha:</label>
          </div>
          <small class="text-muted d-sm-none"
            >sua senha deve ter ao menos 8 caracteres, 1 número e 1
            letra.</small
          >
          <div class="col-sm-6 form-floating">
            <input
              type="floatingPassword"
              v-model="userForm.pass2"
              class="form-control"
              id="floatingPasswordRepeated"
              placeholder="Repita a senha"
              pattern="^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,}$"
              required
            />
            <label for="floatingPasswordRepeated">Repita a senha:</label>
          </div>
          <small class="ps-4text-muted d-none d-sm-block"
            >Sua senha deve ter ao menos 8 caracteres, 1 número e 1
            letra.</small
          >
          <div class="form-floating mb-3 mt-3">
            <input
              type="text"
              v-model="userForm.cpf"
              class="form-control"
              id="floatingcpf"
              placeholder="CPF"
              pattern="^(\d{3})[-.\s]?(\d{3})[-.\s]?(\d{3})[-.\s]?(\d{2})$"
              required
            />
            <label for="floatingcpf">CPF:</label>
          </div>
          <div
            class="alert alert-danger"
            v-if="showErrorMessage"
            id="errorMessage"
          >
            {{ errorMessage }}
          </div>
          <div
            class="alert alert-success"
            v-if="showSuccessMessage"
            id="successMessage"
          >
            {{ successMessage }}
          </div>
          <input
            class="p-2 px-5 w-auto btn btn-primary btn-lg m-auto"
            type="submit"
            value="Criar Conta"
          />
        </form>
        <table id="registers" class="table table-striped mt-5">
          <thead>
            <tr>
              <th scope="col">ID</th>
              <th scope="col">Nome</th>
              <th scope="col">Telefone</th>
              <th scope="col">Nascimento</th>
              <th scope="col">Email</th>
              <th scope="col">CPF</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="user in users" :key="user.id">
              <th scope="row">{{ user.id }}</th>
              <td>{{ user.name }}</td>
              <td>{{ user.phone }}</td>
              <td>{{ user.birthDate }}</td>
              <td>{{ user.email }}</td>
              <td>{{ user.cpf }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </body>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  components: {},
  data: function () {
    return {
      showErrorMessage: false,
      showSuccessMessage: false,
      errorMessage: "Aconteceu algo de errado",
      successMessage: "Conta criada com sucesso! Você pode fazer login agora.",
      userForm: {},
      users: [],
    };
  },
  methods: {
    onSubmit() {
      console.log("submeteu");
      if (this.userForm.pass1 != this.userForm.pass2) {
        this.showErrorMessage = true;
        this.errorMessage = "As senhas não são iguais, por favor verifique.";
      } else {
        this.showErrorMessage = false;
        // this.users.push({
        //   id: this.users.length = 1,
        //   ...this.userForm})
        const data = new URLSearchParams();
        for (var [key, value] of Object.entries(this.userForm)) {
          data.append(key, value);
        }
        //fazer um catch resolvendo possiveis erros
        axios
          .post("http://localhost:9090/users", data)
          .then(() => {
            this.showSuccessMessage = true; // Ativar a mensagem de sucesso
            this.getUsers(); // Atualizar a lista de usuários
          })
          .catch((error) => {
            console.error("Erro ao criar conta:", error);
            this.showErrorMessage = true;
            this.errorMessage =
              "Ocorreu um erro ao criar a conta. Tente novamente.";
          });
      }
    },
    getUsers: function () {
      axios
        .get("http://localhost:9090/users")
        .then((response) => {
          this.users = response.data;
        })
        .catch((error) => {
          console.error("Erro ao obter usuários:", error);
        });
      // var oReq = new XMLHttpRequest();
      // var global = this;

      // oReq.addEventListener("load", function(event){
      //   global.users = JSON.parse(event.target.response)
      // });

      // oReq.open("GET", "http://localhost:9090/users");
      // oReq.send();
    },
  },

  mounted: function () {
    this.getUsers();
  },
};
</script>

<style>
body {
  font-family: "Work Sans", sans-serif;
}

#createAccount label {
  left: auto !important;
}
</style>
