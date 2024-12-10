<!-- eslint-disable no-unused-vars -->
<script setup>
import artistData from './artists'
import songsData from './songs'
import { ref, computed } from 'vue'

const selectedArtist = ref()

const songsOfArtist = computed(() => {
  console.log(selectedArtist)
  if (selectedArtist.value) {
    return songsData.filter((s) => s.ARTIST_ID == selectedArtist.value)
  } else {
    return songsData
  }
})
</script>

<template>
  <div class="container">
    <select class="form-select" v-model="selectedArtist">
      <option value="" selected></option>
      <option v-for="(artist, index) in artistData" :key="index" :value="artist._id">
        {{ artist.artist }}
      </option>
    </select>

    <table class="table">
      <thead>
        <tr>
          <th scope="col">Title</th>
          <th scope="col">TIME</th>
          <th scope="col">BPM</th>
          <th scope="col">YEAR</th>
          <th scope="col">GENRE</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(song, index) in songsOfArtist" :key="index">
          <td>{{ song.TITLE }}</td>
          <td>{{ song.TIME }}</td>
          <td>{{ song.YEAR }}</td>
          <td>{{ song.BPM }}</td>
          <td>{{ song.GENRE }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style></style>
