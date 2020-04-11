<template>
  <div>
    <span class="subtitle">Загрузка треков</span>
    <br />
    <br />

    <div class="control">
      <label class="label" for>Выделите и перенесите все нужные треки</label>
      <input
        accept="audio/*"
        class="input is-primary"
        multiple
        type="file"
        @change="handleFileUploadMusic"
      />
    </div>
    <table v-if="songsList.length">
      <thead>
        <th>Название трека</th>
        <th>Автор музыки</th>
        <th>Автор текста</th>
        <th>Исполнитель</th>
        <th>Изготовитель фонограмм</th>
        <th>Доля авторских/смежных прав</th>
      </thead>
      <tbody>
        <tr
          v-for="songDescription in songsDescriptonsList"
          :key="songDescription.name"
        >
          <td>{{ songDescription.name }}</td>
          <td v-for="fieldName in songDescriptionFieldsNames" :key="fieldName">
            <input
              v-model="songDescription[fieldName]"
              type="text"
              :name="`${songDescription.name}${fieldName}`"
              class="input"
            />
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios';

const SONG_DESCRIPTION_FIELDS = [
  ['melodyAuthor', ''],
  ['textAuthor', ''],
  ['artist', ''],
  ['bitmaker', ''],
  ['rightsParts', '']
];

const getSongDefaultDescription = ({ name }) => {
  return {
    name,

    ...Object.fromEntries(SONG_DESCRIPTION_FIELDS)
  };
};

export default {
  name: 'FormFour',

  data() {
    return {
      songsDescriptonsList: [],
      songsList: [],
      songDescriptionFieldsNames: SONG_DESCRIPTION_FIELDS.map(
        ([fieldName]) => fieldName
      )
    };
  },

  methods: {
    handleFileUploadMusic(event) {
      console.log(event);
      const songsFilesList = Array.from(event.target.files);

      this.songsList = songsFilesList;
      this.songsDescriptonsList = songsFilesList.map(getSongDefaultDescription);
    }
  }
};
</script>
