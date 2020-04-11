<template>
  <div>
    <span class="subtitle">Заполнение персональных данных</span>
    <br />
    <br />
    <div class="control">
      <label class="label">Гражданство</label>
      <input
        type="text"
        v-model="country"
        placeholder="Российской Федерации"
        class="input is-primary"
      />
    </div>

    <div class="columns">
      <div class="column is-half">
        <div class="control">
          <label class="label">ФИО</label>
          <input
            placeholder="Иванов Иван Иванович"
            v-model="authorName"
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
            placeholder="г. Москва"
            v-model="placeOfBirth"
            type="text"
            class="input is-primary"
          />
        </div>
        <div class="control">
          <label class="label">Адрес регистрации</label>
          <input
            placeholder="Как в паспорте"
            v-model="registration"
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
            placeholder="4444"
            v-model="pasportSerie"
            type="number"
            class="input is-primary"
            maxlength="4"
          />
        </div>
        <div class="control">
          <label class="label">Номер паспорта</label>
          <input
            placeholder="666666"
            v-model="pasportNumber"
            type="number"
            class="input is-primary"
            max="6"
          />
        </div>
        <div class="control">
          <label class="label">Кем выдан</label>
          <input
            placeholder="Например: ФМС России"
            v-model="givenBy"
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
      <label class="label"
        for
      >Прикрепите 2 фото паспорта: разворот с фото + страница с регистрацией (на каждого исполнителя)</label>
      <input
        v-on:change="handleFileUpload"
        accept="image/*"
        ref="files"
        class="input is-primary"
        multiple
        type="file"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "formTwo",
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
}
</script>