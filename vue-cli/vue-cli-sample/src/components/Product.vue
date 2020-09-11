<template>
    <div class="product">
        <strong>{{ product.title }}</strong>
        <p>{{ product.description }}</p>
        <strong>Fiyat : {{ product.price }} | Adet : {{ product.count }}</strong>
        <br><br>
        <button @click="addToCart(product)">Sepete Ekle</button>
    </div>
</template>

<script>
export default {
    props: ["product"],
    methods: {
        addToCart(product){
            this.$emit("addToCart", product);
        }
    }
}
</script>

<style>
.product{
    border: 2px dashed #666;
    padding: 5px 10px;
    width: 300px;
    margin-bottom: 5px;
}
.product:hover{
    border: 2px solid #666;
    transition: all .5;
    background-color: antiquewhite;
}
</style>