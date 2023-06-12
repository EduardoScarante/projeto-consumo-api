<script></script>

<template>
  <section>
    <div class="Eduardo">
      <section class="hover">
        <h3>Eduardo Scarante</h3>
        <a href="https://github.com/EduardoScarante" target="_blank"
          ><img src="../imagens/Git.png " width="100"
        /></a>

        <a
          href="https://eduardoscarante.github.io/vuePesonalSite/"
          target="_blank"
        >
          <img src="../imagens/website.png" width="100" />
        </a>
      </section>
      <img src="../imagens/cat.png" />
    </div>

    <div class="Sandy">
      <img src="../imagens/dog.png" />

      <section class="hover">
        <h3>Sandy Seixas</h3>
        <a href="https://github.com/SandySei" target="_blank"
          ><img src="../imagens/Git.png " width="100"
        /></a>

        <a
          href="https://eduardoscarante.github.io/vuePesonalSite/"
          target="_blank"
        >
          <img src="../imagens/website.png" width="100" />
        </a>
      </section>
    </div>
  </section>
</template>

<style scoped>
section {
  display: flex;

  padding-top: 50px;
}
.Eduardo {
  background-color: brown;

  display: flex;
  flex-direction: row;
  justify-content: end;
  align-items: end;

  width: 50vw;
}

.Sandy {
  background-color: rgb(42, 118, 165);

  display: flex;
  flex-direction: row;
  align-items: end;

  width: 50vw;
}
</style>
