<template>
  <section>
    <UsarioForm>
      <button class="btn" @click.prevent="atualizarUsuario">
        Atualizar Usuario
      </button>
    </UsarioForm>
  </section>
</template>

<script>
import UsarioForm from "@/components/UsuarioForm.vue";
import { api } from "@/axios/services.js";

export default {
  name: "UsuarioEditar",
  components: {
    UsarioForm,
  },
  methods: {
    atualizarUsuario() {
      api
        .put(
          `/usuario/${this.$store.state.usuario.id}`,
          this.$store.state.usuario
        )
        .then(() => {
          this.$store.dispatch("getUsuario");
          this.$router.push({ name: "usuario" }).catch((error) => {
            console.log(error.response);
          });
        });
    },
  },
};
</script>

<style></style>
