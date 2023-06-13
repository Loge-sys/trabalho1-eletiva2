<template>
    <footer>
        <h2>Rodapé</h2>
    </footer>
</template>

<script>
export default {
    name: 'Rodape'
}
</script>   

<style scoped>
    footer {
        width: 100%;
        display: flex;
        height: 80px;
        justify-content: center;
        align-items: center;
        background-color: #111;
        position: relative;
        bottom: 0;
    }

    h2 {
        color: #FFFCCC;
        font-size: 15px;
    }
</style>