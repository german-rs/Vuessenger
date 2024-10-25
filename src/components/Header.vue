<script>
</script>
<template>
    <header class="header">
        <h1 class="header__titulo">The 
        <span class="header__titulo header__titulo--degradado">Vuessenger</span> 
        Chat</h1>
    </header>
</template>

<style scoped>
.header{
    padding: 1em;
}
.header__titulo{
    font-family: 'Inter', sans-serif;
    font-weight: 900;
    font-size: 60px;
    text-align: center;
    color: var(--color-gris700);
}
.header__titulo--degradado {
    background: linear-gradient(90deg, var(--color-verde-ligero) , var(--color-azul-ligero));
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent; 
}

@media (min-width: 475px){
    .header__titulo{
        font-size: 65px;
    }
}

@media (min-width: 640px){
    .header__titulo{
        font-size: 70px;
    }
}

@media (min-width: 768px){
    .header__titulo{
        font-size: 75px;
    }
}

@media (min-width: 1024px){
    .header__titulo{
        font-size: 80px;
    }
}
</style>