<template>
  <div>
    <span class="subtitle">Загрузка треков</span>
    <br />
    <br />

    <div class="control">
      <label class="label" for>Выделите и перенесите все нужные треки</label>
      <input
        v-on:change="handleFileUploadMusic"
        accept="audio/*"
        ref="files"
        class="input is-primary"
        multiple
        type="file"
      />
    </div>
    <table v-if="songsList">
      <thead>
        <th>Название трека</th>
        <th>Автор музыки</th>
        <th>Автор текста</th>
        <th>Исполнитель</th>
        <th>Изготовитель фонограмм</th>
        <th>Доля авторских/смежных прав</th>
      </thead>
      <tbody>
        <tr v-for="song in Array.from(songsList)" v-bind:key="song">
          <td>{{ song.name }}</td>
          <td>
            <input type="text" class="input" />
          </td>
          <td>
            <input type="text" class="input" />
          </td>
          <td>
            <input type="text" class="input" />
          </td>
          <td>
            <input type="text" class="input" />
          </td>
          <td>
            <input type="text" class="input" />
          </td>
          
        </tr>
      </tbody>
    </table>
    
  </div>
</template>

<script>
export default {
  name: "formFour",
  props: {
    songsList: FileList,
    songsTableData: Array
  },
  methods: {
    handleFileUploadMusic() {
      this.songsList = this.$refs.files.files;
    }
  }
};
</script>