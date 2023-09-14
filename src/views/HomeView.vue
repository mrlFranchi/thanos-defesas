<template>
  <div>
  <v-main style="padding: 0;">
    <v-app-bar
    clipped-left
    clipped-right>
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
      temporary>
      <v-card>
        <v-list-group
          :value="true"
        >
          <template v-slot:activator>
            <v-list-item-title>Programas</v-list-item-title>
          </template>
            <v-radio-group
            v-model="programa">
              <v-radio
                v-for="n in programas"
                :key="n"
                :label="`${n}`"
                :value="n"
                @click="click(programa)"
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
            v-model="curso">
              <v-radio
                v-for="n in cursos"
                :key="n"
                :label="`${n}`"
                :value="n"
                @click="click(curso)"
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
      width = "25%"
    >
      <CardDefesa
      :defesa = "selectedRow"
      />
    </v-navigation-drawer>
    <v-card height = "800px">
      <v-card-title>
        Filtrando por curso: {{ this.curso }}, do programa: {{ this.programa }}
      </v-card-title>
      <v-data-table
      :headers="headers"
      :items="defesas"
      :search="nome"
      @click:row="select_row"
      >
      <template v-slot:[`item.Data`]="{ item }">
        <span>{{ item.Data.toLocaleDateString() }}</span>
      </template>
    </v-data-table>
    </v-card>
  </v-main>
  </div>
</template>

<script>
import CardDefesa from '@/components/CardDefesa.vue';

export default {
  data() {
    return {
      drawer: false,
      rightDrawer: false,
      nome: '',
      programas: ['Todos', 'MAT', 'CCMC', 'PIPGEs', 'PROFMAT'],
      programa: 'Todos',
      cursos: ['Todos', 'Mestrado', 'Doutorado', 'DD'],
      curso: 'Todos',
      selectedRow: undefined,
      headers: [
        {
          text: 'Nome', value: 'Nome', filterable: true,
        },
        {
          text: 'Curso',
          value: 'Curso',
          filterable: true,
          filter: (value) => (this.curso === 'Todos' || value === this.curso),
        },
        {
          text: 'Programa',
          value: 'Programa',
          filterable: true,
          filter: (value) => (this.programa === 'Todos' || value === this.programa),
        },
        {
          text: 'Orientador', value: 'Orientador', filterable: false,
        },
        {
          text: 'Data', value: 'Data', filterable: false,
        },
      ],
      defesas: undefined,
      filtered: undefined,
    };
  },
  methods: {
    click(c) {
      console.log(c);
    },
    select_row(r) {
      this.rightDrawer = true;
      this.selectedRow = r;
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
      this.defesas.forEach((e) => {
        const data = e.Data.split('/');
        e.Data = new Date(data[2], data[1] - 1, data[0]);
        // e.Data = e.Date.toLocaleDateString();
      });
    },

  },
  beforeMount() {
    this.get_data();
  },
  components: {
    CardDefesa,
  },
};
</script>
