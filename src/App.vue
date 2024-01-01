<script setup lang="ts">
import { ref } from 'vue';

import Input from './components/Input.vue';
import Select from './components/Select.vue';

const name = ref('');
const password = ref('');
const option = ref('');

const items = [
  {
    icon: 'ph:user',
    name: 'Usuarios',
    value: 'users'
  },
  {
    icon: 'ph:file',
    name: 'Documentos',
    value: 'documents'
  },
  {
    icon: 'ph:music-note',
    name: 'Músicas',
    value: 'musics'
  },
]
</script>

<template>
  <main>
    <section>
      <h1 class="text-primary">Formulário</h1>

      <hr />

      <Input
        id="name"
        icon="ph:user"
        placeholder="Nome Completo"
        v-model="name"
      />

      <Input
        id="password"
        icon="ph:lock"
        placeholder="Senha"
        type="password"
        v-model="password"
      />

      <div class="select-container">
        <Select
          label="Selecione"
          :items="items"
          @change="(value) => option = value"
        />

        <Select
          label="Selecione"
          :items="items"
          @change="(value) => option = value"
        />
      </div>

      <Select
        label="Selecione"
        :items="items"
        @change="(value) => option = value"
      />
    </section>

    <section>
      <h1 class="text-secondary">Dados</h1>

      <hr />

      Nome: <span>{{ name }}</span>
      Senha: <span>{{ password }}</span>
      Selecionado: <span>{{ option }}</span>
    </section>
  </main>
</template>

<style scoped lang="scss">
  @import './assets/colors.scss';

  main {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100dvh;

    section {
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
      padding: 1rem;
      border-radius: 10px 0 0 10px;
      background-color: $bg-color-s;
      border: 1px solid black;
      box-shadow: 5px 5px 15px rgb(18 18 18 / 50%);
      width: min(25rem, 100%);
      aspect-ratio: 2 / 1;

      &:last-child {
        border-radius: 0 10px 10px 0;
      }

      .select-container {
        display: flex;
        gap: 0.5rem;
      }
    }
  }
</style>
