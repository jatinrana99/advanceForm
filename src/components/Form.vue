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
    background: linear-gradient(0.25turn, #91e3ab, #ebf8e1, #91cb70b7);

}
</style>