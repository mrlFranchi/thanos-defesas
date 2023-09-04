<template>
    <v-card>
        <v-icon  class="text-center" size="300">mdi-account</v-icon>
        <v-card-title class="text-center">
            {{  defesa.Nome  }}
        </v-card-title>
        <v-card-subtitle>
          {{ curso }} em {{ programa }} na data de {{ defesa.Data }}
        </v-card-subtitle>
        <v-card-text v-show="orientador">
          Orientador: {{ defesa.Orientador }}
        </v-card-text>
        <v-card-actions>
          <v-btn>
            <img src="./../assets/Dedalus.png"
            width = "100" height = "30"
            alt="Logo do Dedalus-USP">
          </v-btn>
        </v-card-actions>
    </v-card>
</template>
<script>
export default {
  data() {
    return {
      programa: '',
      curso: '',
      orientador: false,
    };
  },
  methods: {
    click(c) {
      console.log(c);
    },
    arruma() {
      if (this.defesa.Curso === 'DD') {
        this.curso = 'Doutorado Direto';
      } else {
        this.curso = this.defesa.Curso;
      }
      switch (this.defesa.Programa) {
        case 'MAT':
          this.programa = 'Matemática';
          break;
        case 'CCMC':
          this.programa = 'Ciência da Computação e Matemática Computacional';
          break;
        case 'PIPGEs':
          this.programa = 'Programa Interinstitucional de Pós-Graduação em Estatística UFSCar-USP';
          break;
        case 'PROFMAT':
          this.programa = 'Mestrado Profissional em Matemática em Rede Nacional';
          break;
        default:
          this.programa = this.defesa.Programa;
      }
      this.orientador = !(this.defesa.Orientador === '');
    },
  },
  props: [
    'defesa',
  ],
  afterMount() {
    this.arruma();
  },
  beforeUpdate() {
    this.arruma();
  },
};
</script>
