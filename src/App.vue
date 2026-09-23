<script setup>
  import { ref, onMounted, onUnmounted } from 'vue'

  const windowWidth = ref(window.innerWidth)

  function updateWidth() {
    windowWidth.value = window.innerWidth
  }

  onMounted(() => {
    window.addEventListener('resize', updateWidth)
  })

  onUnmounted(() => {
    window.removeEventListener('resize', updateWidth)
  })

  function goToGoogle() {
    window.location.href = 'https://search.google.com/local/writereview?placeid=ChIJc8ITqRVPYA0R2mx4toQGrXo'
  }

</script>

<template>
  <main class="page">

    <section class="review-card">

      <!-- CABECERA -->
      <header class="header">

        <img
          src="./assets/logo-sra.jpeg"
          alt="Sales Rodríguez Administradores"
          class="logo"
        />

      </header>

      <!-- CONTENIDO -->
      <section class="content">

        <p class="eyebrow">
          SU OPINIÓN NOS IMPORTA
        </p>

        <h1>
          ¿Cómo ha sido su<br />
          experiencia con nosotros?
        </h1>

        <!-- <p class="description">
          Su opinión nos ayuda a seguir ofreciendo
          un servicio cada vez mejor.
        </p> -->
        <!-- TEXTO PARA MÓVIL -->
        <p v-if="windowWidth < 768" class="description">
          Su opinión nos ayuda a seguir<br />
          ofreciendo un servicio<br />
          cada vez mejor.
        </p>

        <!-- TEXTO PARA TABLET Y PC -->
        <p v-else class="description">
          Su opinión nos ayuda a seguir ofreciendo<br />
          un servicio cada vez mejor.
        </p>

        <!-- ESTRELLAS -->
        <div class="stars">

          <button
            v-for="star in 5"
            :key="star"
            class="star"
            @click="goToGoogle"
            :aria-label="`${star} estrellas`"
          >
            ★
          </button>

        </div>

        <p class="rating-text">
          Seleccione una valoración
        </p>

      </section>

    </section>

  </main>
</template>

