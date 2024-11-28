<template>
    <div class="container">
        <h4>Nhập tháng</h4>
        <input type = "number" v-model.number = "month">
        <p v-if="month < 1 || month > 12" class = "text-danger">Vui lòng nhập lại tháng từ 1 đến 12</p>
        <p v-else-if= "month <= 3">Mùa xuân</p>
        <p v-else-if= "month <= 6">Mùa hạ</p>
        <p v-else-if= "month <= 9">Mùa thu</p>
        <p v-else>Mùa đông</p>
    </div>
</template>

<script setup>
    import { ref } from 'vue';
    const month = ref(1)
</script>