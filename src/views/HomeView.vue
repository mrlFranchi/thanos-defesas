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
          v-model="programa">
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
          v-model="curso">
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
