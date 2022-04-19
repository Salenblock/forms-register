<template>
  <div class="container mt-4">
    <div class="row">
      <div class="col-sm-4 mx-auto">
        <form @submit.prevent="registerUser" novalidate>
          <div v-show="step === 1" class="step">
            <h6>Основные данные</h6>

            <div class="form-group">
              <label for="name" class="form-label">Ваше имя</label>
              <input v-model='formReg.name' type="text" class="form-control is-invalid" id="name"
                aria-describedby="nameFeedback" required placeholder="Ваше имя">
              <div id="nameFeedback" class="invalid-feedback">
                *Поле обязательное для заполнения.
              </div>
            </div>

            <div class="form-group">
              <label for="surname" class="form-label">Ваша фамилия</label>
              <input v-model='formReg.surname' type="text" class="form-control is-invalid" id="surname"
                aria-describedby="surnameFeedback" required placeholder="Ваша фамилия">
              <div id="surnameFeedback" class="invalid-feedback">
                *Поле обязательное для заполнения.
              </div>
            </div>

            <div class="form-group">
              <label for="patronymic">Ваше отчество</label>
              <input v-model='formReg.patronymic' type="text" class="form-control" id="patronymic"
                placeholder="Ваше отчество">
            </div>

            <div class="form-group">
              <label for="date" class="form-label">Дата рождения:</label>
              <input v-model='formReg.date' type="date" class="form-control is-invalid" id="date"
                aria-describedby="dateFeedback" required>
              <div id="dateFeedback" class="invalid-feedback">
                *Поле обязательное для заполнения.
              </div>
            </div>

            <div class="form-group">
              <label for="phone" class="form-label">Номер телефона</label>
              <input v-model='formReg.phone' type="tel" class="form-control is-invalid" id="phone"
                aria-describedby="phoneFeedback" required placeholder="+7(XXX)XXX-XX-XX">
              <div id="phoneFeedback" class="invalid-feedback">
                *Поле обязательное для заполнения.
              </div>
            </div>



            <div class="checkbox-pol">
              <input v-model='formReg.exampleCheck1' type="checkbox" class="form-check-input" id="exampleCheck1">
              <label class="form-check-label" for="exampleCheck1">М</label>
              <input v-model='formReg.exampleCheck1' type="checkbox" class="form-check-input" id="exampleCheck1">
              <label class="form-check-label" for="exampleCheck1">Ж</label>
            </div>

            <label for="team">Группа клиентов</label>
            <div class="col-md-4">
              <select id="inputState" class="form-select" multiple data-mdb-placeholder="Example placeholder" size="2">
                <option selected>Выберите...</option>
                <option>Иванов</option>
                <option>Захаров</option>
                <option>Чернышева</option>
              </select>
            </div>

            <div class="col-md-4">
              <label for="inputState" class="form-label">Лечащий врач</label>
              <select id="inputState" class="form-select">
                <option selected>Выберите...</option>
                <option>Иванов</option>
                <option>Захаров</option>
                <option>Чернышева</option>
              </select>

            </div>

            <div class="checkboxSMS">
              <input type="checkbox" class="form-check-input" id="exampleCheck1">
              <label class="form-check-label" for="exampleCheck1">Не отправлять СМС</label>
            </div>

            <button @click="nextStep" type="button" class="btn btn-outline-success ">Следующий шаг</button>

          </div>

          <transition name="slide-fade">
            <div v-show="step === 2" class="step">
              <h6>Адрес</h6>
              <div class="form-group">
                <label for="index">Индекс</label>
                <input type="text" class="form-control" id="index">
              </div>

              <div class="form-group">
                <label for="country">Страна</label>
                <input type="text" class="form-control" id="country">
              </div>

              <div class="form-group">
                <label for="region">Область</label>
                <input type="text" class="form-control" id="region">
              </div>


              <div class="form-group">
                <label for="city" class="form-label">Номер телефона</label>
                <input v-model='formReg.city' type="text" class="form-control is-invalid" id="city"
                  aria-describedby="cityFeedback" required placeholder="Ваш город">
                <div id="cityFeedback" class="invalid-feedback">
                  *Поле обязательное для заполнения.
                </div>
              </div>


              <div class="form-group">
                <label for="street">Улица</label>
                <input type="text" class="form-control" id="street">
              </div>

              <div class="form-group">
                <label for="home">Дом</label>
                <input type="text" class="form-control" id="home">
              </div>


              <button @click="backStep" type="button" class="btn btn-outline-primary ">Назад</button>
              <button @click="nextStep" type="button" class="btn btn-outline-success mr-2 ">Следующий шаг</button>

            </div>
          </transition>

          <transition name="slide-fade">
            <div v-show="step === 3" class="step">
              <h6>Личные данные</h6>

              <div class="col-md-4">
                <label for="inputState" class="form-label">Тип документа</label>
                <select id="inputState" class="form-select">
                  <option selected>Выберите...</option>
                  <option>Паспорт</option>
                  <option>Свидетельство о рождении</option>
                  <option>Вод. удостоверение</option>
                </select>
              </div>


              <div class="form-group">
                <label for="series">Серия</label>
                <input type="text" class="form-control" id="series">
              </div>

              <div class="form-group">
                <label for="number">Номер</label>
                <input type="text" class="form-control" id="number">
              </div>

              <div class="form-group">
                <label for="issued">Кем выдан</label>
                <input type="text" class="form-control" id="issued">
              </div>

              <div class="form-group">
                <label for="date" class="form-label">Дата выдачи</label>
                <input v-model='formReg.date' type="date" class="form-control is-invalid" id="date"
                  aria-describedby="dateFeedback" required >
                <div id="dateFeedback" class="invalid-feedback">
                  *Поле обязательное для заполнения.
                </div>
              </div>

              <button @click="backStep" type="button" class="btn btn-outline-primary ">Назад</button>
              <button type="submit" class="btn btn-outline-success mr-2">Зарегистрироваться</button>
              
            </div>
          </transition>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
  export default {

    data() {
      return {
        step: 1,
        formReg: {
          name: '',
          surname: '',
          email: '',
          password: '',
          passwordConfirm: '',
          country: '',
          city: '',
        }
      }
    },
    methods: {
      nextStep() {
        if (this.step < 3) {
          this.step++
        }
      },
      backStep() {
        if (this.step > 1) {
          this.step--
        }
      },
      registerUser() {
        console.log('Регистрация прошла успешно!')
        console.log(this.formReg.name)
      }
    },
    validations: {

    }
  }
</script>

<style>
  .checkbox-pol label {
    margin: 0px 20px 5px 3px;
  }

  .form-group label {
    margin: 0px 0px 5px 0px;
  }

  .form-group input {
    margin: 0px 0px 15px 0px;
  }

  .form-group select {
    margin: 0px 0px 10px 0px;
  }

  .checkboxSMS label {
    margin: 0px 20px 5px 3px;
  }

  .mr-2 {
    margin: 0px 0px 0px 10px;
    ;
  }

  .slide-fade-enter-active {
    transition: all 0.3s ease;
  }

  .slide-fade-enter {
    transform: translateX(10px);
    opacity: 0;
  }
</style>