<template>
  <div id="app">
    <div class="container">
      <h1>Listado Cursos</h1>
      <div class="cursos">
        <ul>
          <mi-componente
            v-for="(item, key) in Cursos"
            :key="key"
            :itemCurso="{ indice: key, ...item }"
          />
        </ul>
        <p class="cursos__total">
          Horas acumuladas de cursos: {{ totalHoras }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import miComponente from '@/components/miComponente.vue'
export default {
  name: 'App',
  data() {
    return {
      Cursos: [
        {
          plataformas: ['Platzi', 'Youtube', 'Instagram'],
          nombre: 'Figma',
          horas: 40,
        },
        {
          plataformas: [
            'Platzi',
            'Youtube',
            'Instagram',
            'Codigo Facilito',
            'Udemy',
          ],
          nombre: 'Javascript',
          horas: 80,
        },
        {
          plataformas: [
            'Platzi',
            'Youtube',
            'Vuemastery',
            'vueschool',
            'Github',
            'Udemy',
          ],
          nombre: 'Vuejs',
          horas: 75,
        },
        {
          plataformas: ['Platzi', 'Youtube', 'Instagram', 'Codelytv'],
          nombre: 'CSS',
          horas: 95,
        },
      ],
    }
  },
  components: {
    miComponente,
  },
  computed: {
    totalHoras: function () {
      const reducir = (acum, { horas }) => acum + horas
      return this.Cursos.reduce(reducir, 0)
    },
  },
}
</script>

<style lang="scss">
body {
  background: khaki;
  font-family: BlinkMacSystemFont, -apple-system, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    'Helvetica', 'Arial', sans-serif;
}
.container {
  width: 100%;
  max-width: 600px;
  margin: 0px auto;
}
H1 {
  text-align: center;
}
.cursos {
  background: white;
  margin-top: 2rem;
  padding: 1.4rem;
  border-radius: 1rem;
  box-shadow: 0 1.4px 3.4px rgba(88, 88, 88, 0.045),
    0 3.3px 8.2px rgba(82, 82, 82, 0.065),
    0 6.1px 15.5px rgba(105, 105, 105, 0.08),
    0 10.9px 27.7px rgba(0, 0, 0, 0.095), 0 20.5px 51.8px rgba(0, 0, 0, 0.115),
    0 49px 124px rgba(90, 90, 90, 0.16);
  &__ul {
    list-style: none;
  }
  &__li {
    display: grid;
    grid-template-areas: 'numero nombre plata horas';
    grid-auto-columns: 50px auto auto 60px;
    color: #333;
    border-bottom: 1px solid #ccc;
    border-radius: 0.4rem;
    margin-bottom: 1rem;
    font-weight: bold;
    padding: 0.5rem;
  }
  &__num {
    grid-area: numero;
    text-align: left;
  }
  &__nombre {
    grid-area: nombre;
    text-align: left;
  }
  &__plataformas {
    grid-area: plata;
    display: flex;
    flex-direction: column;
    font-weight: normal;
    font-size: 0.9rem;
    p {
      color: grey;
      padding: 0;
      margin: 0;
    }
  }

  &__horas {
    grid-area: horas;
    text-align: right;
  }

  &__total {
    text-align: center;
  }
}
</style>
