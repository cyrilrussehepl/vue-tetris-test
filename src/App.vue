<script>
import HelloWorld from './components/HelloWorld.vue'
import Jeu from './components/Jeu.vue'
import TheWelcome from './components/TheWelcome.vue'

import { ref, onMounted } from "vue";

export default {
  setup() {
    const monFormulaire = ref(null);

    onMounted(() => {
      setupForm();
    });

    const setupForm = () => {
      const form = document.querySelector("#formTest");
      if (form) {
        form.addEventListener("submit", submitForm);
      } else {
        console.error("Le formulaire n'a pas pu être trouvé.");
      }
    };

    const submitForm = (event) => {
      event.preventDefault();
      // Logique de traitement du formulaire
      const data = {
    username: "Romain",
    password: "mdp"
  };

  // Register api endpoint
  const url = "https://europe-west1.gcp.data.mongodb-api.com/app/application-0-ptcis/endpoint/register"; 

  // Effectuez la requête POST
  fetch(url, {
    method: "POST",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify(data)
  })
    .then(response => response.json())
    .then(result => {
      console.log("Réponse du serveur :", result);
      // Faites quelque chose avec la réponse du serveur
    })
    .catch(error => {
      console.error("Erreur lors de la requête :", error);
      // Gérez les erreurs de requête
    });
    };

    return {
      monFormulaire
    };
  }
};


</script>

<template>
  <main>
    <form action="post" id="formTest">
      <button type="submit">Test</button>
    </form>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
