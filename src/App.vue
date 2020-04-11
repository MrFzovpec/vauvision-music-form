<template>
  <div id="app">
    <Menu></Menu>
    <section class="content section container">
      <div id="content">
        <form ref="form" @submit.prevent="onSubmit">
          <h2 class="title is-3">Заявка на регистрацию треков</h2>

          <FirstPage
            v-if="pageNumber == 1"
            :release-info="form.releaseInfo"
            @update="updateReleaseInfo"
          />

          <SecondPage v-if="pageNumber == 2"></SecondPage>
          <ThirdPage v-if="pageNumber == 3"></ThirdPage>
          <ForthPage v-if="pageNumber == 4"></ForthPage>

          <section class="buttons">
            <div
              v-if="pageNumber >= 2"
              class="button is-danger"
              @click="prevPage"
            >
              Назад
            </div>
            <div
              v-if="pageNumber <= 6"
              class="button is-primary"
              @click="nextPage"
            >
              Далее
            </div>
            <button type="submit">asdfdsaf</button>
          </section>
        </form>
      </div>
    </section>
  </div>
</template>

<script>
import axios from 'axios';

import Menu from './components/Menu';

import FirstPage from './components/formPageOne';
import SecondPage from './components/formPageTwo';
import ThirdPage from './components/formPageThree';
import ForthPage from './components/formPageFour';

export default {
  name: 'App',
  components: {
    Menu,
    FirstPage,
    SecondPage,
    ThirdPage,
    ForthPage
  },

  data() {
    return {
      pageNumber: 1,

      form: {
        releaseInfo: {
          releaseType: null,
          releaseName: ''
        }
      }
    };
  },

  methods: {
    nextPage: function() {
      this.pageNumber = this.pageNumber + 1;
    },

    prevPage: function() {
      this.pageNumber = this.pageNumber - 1;
    },

    updateReleaseInfo(updatedInfo) {
      this.form.releaseInfo = updatedInfo;
    },

    onSubmit() {
      axios.post('/api/');
    }
  }
};
</script>

<style lang="scss">
$font: Avenir, Helvetica, Arial, sans-serif;
$color: #2c3e50;
#app section.content {
  min-height: 90vh;
  display: flex;
}
#content {
  display: flex;
  justify-content: center;
  align-items: center;
}
div.is-danger {
  margin-right: 5%;
}
div.control {
  margin-bottom: 15px;
}
.buttons {
  margin-top: 3%;
}
</style>
