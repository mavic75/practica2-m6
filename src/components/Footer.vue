<template>
    <footer :style="`background-color: ${colorFooter};`">

	</footer>
</template>

<script>
export default {
    name: "Footer",
    props: ["incolorFooter"],
    emits: ["on-colorFooter"],
    data() {
        return {
            colorFooter: "" 
        }
    },
    mounted() {
        this.colorFooter = this.incolorFooter;
    },
}
</script>

<style>

</style>