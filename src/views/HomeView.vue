<template>
  <div>
  <v-main style="padding: 0;">
    <v-app-bar
    clipped-left>
    <v-btn @click="drawer = !drawer">Filtros</v-btn>

    <v-spacer/>

    <v-toolbar-title><v-text-field
      label="Busca por nome"
      v-model="nome"
      single-line
    /></v-toolbar-title>
    <v-spacer/>
    </v-app-bar>
    <v-navigation-drawer
      v-model="drawer"
      absolute
      temporary
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
    <v-navigation-drawer
      v-model="rightDrawer"
      absolute
      temporary
      right
    >
      <v-card>
        teste
      </v-card>
    </v-navigation-drawer>
    <v-card>
      <v-card-title>
      </v-card-title>
      <v-data-table
      dense
      :headers="headers"
      :items="defesas"
      :search="nome"
      ></v-data-table>
    </v-card>
  </v-main>
  </div>
</template>

<script>
export default {
  data: () => ({
    drawer: false,
    rightDrawer: false,
    nome: '',
    programas: ['Todos', 'MAT', 'CCMC', 'PIPGEs', 'PROFMAT'],
    programa: 'Todos',
    cursos: ['Todos', 'Mestrado', 'Doutorado', 'DD'],
    curso: 'Todos',
    headers: [
      {
        text: 'Ordem', value: 'Ordem', filterable: true,
      },
      {
        text: 'Nome', value: 'Nome', filterable: true,
      },
      {
        text: 'Curso',
        value: 'Curso',
      },
      {
        text: 'Programa',
        value: 'Programa',
      },
      {
        text: 'Data', value: 'Data', filterable: true,
      },
    ],
    defesas: undefined,
    filtered: undefined,
  }),
  methods: {
    click() {
      console.log(this.programa);
    },
    async filter() {
      this.filtered = [];
      for (let i = 0; i < this.defesas.length; i += 1) {
        if ((this.programa === 'Todos' || this.defesas[i].Programa === this.programa)
            && (this.curso === 'Todos' || this.defesas[i].Curso === this.curso)) {
          this.filtered.push(this.defesas);
        }
      }
    },

    async get_data() {
      const url = 'http://127.0.0.1:5000/get_json';
      const response = await fetch(url);
      this.defesas = await response.json();
      this.defesas = this.defesas.items;
    },

  },
  beforeMount() {
    this.get_data();
    // this.filter();
  },
};
</script>
