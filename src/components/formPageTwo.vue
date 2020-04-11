<template>
  <div>
    <span class="subtitle">Заполнение персональных данных</span>
    <br />
    <br />
    <div class="control">
      <label class="label">Гражданство</label>
      <input
        v-model="country"
        type="text"
        placeholder="Российской Федерации"
        class="input is-primary"
      />
    </div>

    <div class="columns">
      <div class="column is-half">
        <div class="control">
          <label class="label">ФИО</label>
          <input
            v-model="authorName"
            placeholder="Иванов Иван Иванович"
            type="text"
            class="input is-primary"
          />
        </div>
        <div class="control">
          <label class="label">Дата рождения</label>
          <input v-model="dateOfBirth" type="date" class="input is-primary" />
        </div>
        <div class="control">
          <label class="label">Место рождения</label>
          <input
            v-model="placeOfBirth"
            placeholder="г. Москва"
            type="text"
            class="input is-primary"
          />
        </div>
        <div class="control">
          <label class="label">Адрес регистрации</label>
          <input
            v-model="registration"
            placeholder="Как в паспорте"
            type="text"
            class="input is-primary"
            max="6"
          />
        </div>
      </div>
      <div class="column is-half">
        <div class="control">
          <label class="label">Серия паспорта</label>
          <input
            v-model="pasportSerie"
            placeholder="4444"
            type="number"
            class="input is-primary"
            maxlength="4"
          />
        </div>
        <div class="control">
          <label class="label">Номер паспорта</label>
          <input
            v-model="pasportNumber"
            placeholder="666666"
            type="number"
            class="input is-primary"
            max="6"
          />
        </div>
        <div class="control">
          <label class="label">Кем выдан</label>
          <input
            v-model="givenBy"
            placeholder="Например: ФМС России"
            type="text"
            class="input is-primary"
            max="6"
          />
        </div>
        <div class="control">
          <label class="label">Когда выдан</label>
          <input v-model="givenAt" type="date" class="input is-primary" />
        </div>
      </div>
    </div>
    <div class="control">
      <label class="label" for
        >Прикрепите 2 фото паспорта: разворот с фото + страница с регистрацией
        (на каждого исполнителя)</label
      >
      <input
        ref="files"
        accept="image/*"
        class="input is-primary"
        multiple
        type="file"
        @change="handleFileUpload"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'FormTwo',
  props: {
    authorName: String,
    dateOfBirth: Date,
    placeOfBirth: String,
    pasportSerie: Number,
    pasportNumber: Number,
    givenBy: String,
    givenAt: Date,
    registration: String,
    country: String,
    passportScans: FileList
  },
  methods: {
    handleFileUpload() {
      this.passportScans = this.$refs.files.files;
    }
  }
};
</script>
