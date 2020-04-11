<template>
  <div>
    <span class="subtitle">Заполнение данных о релизе</span>
    <br />
    <br />
    <label class="label">Выберите тип релиза</label>
    <div class="select is-primary">
      <select
        :value="releaseInfo.releaseType"
        @input="updateInfo('releaseType', $event)"
      >
        <option>Сингл</option>
        <option>EP</option>
        <option>Сингл + EP</option>
      </select>
    </div>
    <br />
    <br />
    <div v-if="releaseInfo.releaseType">
      <label for class="label"
        >Впишите "Псевдоним артиста – Название сингла/альбома" (если это
        совместный трек – пишите артистов через запятую, если это фит, то через
        "feat.", если нужно указать продакшн – впишите продакшн)</label
      >
      <input
        :value="releaseInfo.releaseName"
        class="input is-primary"
        placeholder="Например: PHARAOH feat. Молодой Платон – Тост"
        type="text"
        @input="updateInfo"
      />
      <br />
      <br />
      <label for class="label">В треках есть мат?</label>
      <div class="control">
        <label class="radio">
          <input v-model="filthy" value="true" type="radio" name="answer" />
          Да
        </label>
        <label class="radio">
          <input v-model="filthy" value="false" type="radio" name="answer" />
          Нет
        </label>
        <br />
      </div>

      <div v-if="filthy == 'true'">
        <br />
        <label class="label" for
          >Укажите через запятую номера треков, где есть мат</label
        >
        <input
          v-model="filthyTracks"
          placeholder="Например: 1, 2, 4"
          class="input is-primary"
          type="text"
        />
      </div>
      <br />
      <label for class="label"
        >Желаемая дата выхода (если всё равно, ставьте ближайшую пятницу)</label
      >
      <input v-model="releaseDate" type="date" class="input is-primary" />
      <br />
      <br />
      <label for class="label">На какие площадки заливать?</label>
      <div class="select is-primary">
        <select v-model="releasePlace">
          <option>На все площадки</option>
          <option>Только на BOOM</option>
          <option>На все, кроме BOOM</option>
        </select>
      </div>
      <br />
      <br />
      <label for class="label">Дополнительные комментарии</label>
      <textarea
        id
        name
        class="textarea is-primary"
        cols="30"
        rows="10"
      ></textarea>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FormFirst',

  props: {
    releaseInfo: {
      type: Object,
      required: true
    }
  },

  data() {},

  methods: {
    updateInfo(fieldName, { target }) {
      const { value } = target;

      const updatedInfo = {
        ...this.releaseInfo,
        [fieldName]: value
      };

      this.$emit('update', updatedInfo);
    }
  }
};
</script>
