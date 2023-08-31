<template>
  <v-main style="padding: 0;">
  <v-toolbar>
    <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

    <v-spacer/>

    <v-toolbar-title><v-text-field
      label="Busca por nome"
      v-model="nome"
      single-line
    /></v-toolbar-title>
    <v-spacer/>
  </v-toolbar>
  <v-navigation-drawer
    v-model="drawer"
  >
  <v-card>
    <v-list-group
      :value="true"
    >
      <template v-slot:activator>
        <v-list-item-title>Programas</v-list-item-title>
      </template>
        <v-radio-group
        v-model="programa"
        @click="console.log(programa)">
          <v-radio
            v-for="n in programas"
            :key="n"
            :label="`${n}`"
            :value="n"
            @click="click"
          ></v-radio>
        </v-radio-group>
    </v-list-group>
  </v-card>
  <v-card>
    <v-list-group
      :value="true"
    >
      <template v-slot:activator>
        <v-list-item-title>Cursos</v-list-item-title>
      </template>
        <v-radio-group
        v-model="curso"
        @click="console.log(curso)">
          <v-radio
            v-for="n in cursos"
            :key="n"
            :label="`${n}`"
            :value="n"
            @click="click"
          ></v-radio>
        </v-radio-group>
    </v-list-group>
  </v-card>
  </v-navigation-drawer>
    <!--  -->
  </v-main>
</template>

<script>
export default {
  data: () => ({
    drawer: false,
    nome: '',
    programas: ['Todos', 'MAT', 'CCMC', 'PIPGEs', 'PROFMAT'],
    programa: 'Todos',
    cursos: ['Todos', 'Mestrado', 'Doutorado'],
    curso: 'Todos',

  }),
  methods: {
    click() {
      console.log(this.programa);
    },
  },
};
</script>
