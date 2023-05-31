<template>
    <div id="form">
        <header>
            <slot name="header"></slot>
        </header>
        <section>
            <slot name="body"></slot>
        </section>
        <footer>
            <slot name="footer"></slot>
        </footer>
    </div>

    <div>
        
    </div>
</template>

<script>

export default {
    name:`Form`,
    components:{
    },

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