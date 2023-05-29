<template>
    <div id="form">
        <header>
            <slot name="header"></slot>
        </header>
        <body>
            <slot name="body"></slot>
        </body>
        <footer>
            <slot name="footer"></slot>
        </footer>
    </div>
</template>

<script>
export default {
    name:`Form`
}
</script>


<style scoped>
#form{
    width: 456px;
    border: 2px solid;
    display: inline-block;
}
</style>