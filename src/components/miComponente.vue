<template>
  <li class="cursos__li">
    <div class="cursos__num">{{ itemCurso.indice + 1 }}</div>
    <div class="cursos__nombre">{{ itemCurso.nombre }}</div>
    <div class="cursos__plataformas">
      <p>Plataformas:</p>
      <div
        class="cursos__plataforma"
        v-for="(item, key) in itemCurso.plataformas"
        :key="key"
      >
        - {{ item }}
      </div>
    </div>
    <div class="cursos__horas">{{ itemCurso.horas }} Hrs.</div>
  </li>
</template>

<script>
export default {
  props: {
    itemCurso: {
      type: Object,
    },
  },
}
</script>
