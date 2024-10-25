<script></script>
<template>
    <footer class="footer" >
        <img class="footer__img" src="../assets/logo.svg" alt="Logo de VueJS">
        <p class="footer__texto" >The <span class="footer__texto--degradado">Vuessenger</span> Chat</p>
    </footer>
</template>
<style scoped>
.footer{
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
    align-items: center;
    padding-top: 5em;
    padding-bottom: 2em;
    gap: 1em;
    background-color: var(--color-fondo-footer);
}

.footer__img{
    width: 60px;
}

.footer__texto{
    font-weight: 800;
    color: var(--color-gris400);
    letter-spacing: 1px;
}

.footer__texto--degradado {
    background: linear-gradient(90deg, var(--color-verde-ligero) , var(--color-azul-ligero));
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent; 
    font-weight: 800;
    letter-spacing: 1px;
}
</style>