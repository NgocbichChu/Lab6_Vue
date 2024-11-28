<template>
    <div class="container">
        <h2 class="text-center">Kiến thức sức khỏe cộng đồng</h2>
        <div class="row">
            <div class="col-sm-4 mb-4" v-for="(item, index) in items" :key="index">
                <div class="card">
                    <img :src="item.image" class="img-fluid">
                    <div class="card-body">
                        <h4 class="card-title">{{ item.title }}</h4>
                        <p class="card-text">{{ item.content }}</p>
                        <button class="btn btn-primary">Xem chi tiết </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
    import img1 from '../components/images/img1.png'
    import img2 from '../components/images/img2.jpg'
    import img3 from '../components/images/img3.png'

    const items = ([
        {title: '8 loại rau củ quả giàu canxi', content: 'Canxi là khoáng chất cần thiết đối với cơ thể người. Có nhiều cách để bổ sung canxi, trong đó bổ sung qua đường ăn uống là cách tốt nhất. Có 8 loại rau củ giàu canxi nên ăn hàng ngày...', image: img1},
        {title: 'Các loại gia vị tốt cho sức khỏe', content: 'Một số loại gia vị cung cấp nhiều polyphenol chống oxy hóa cao hơn các loại gia vị quen thuộc khác. Với một lượng nhỏ các món ăn đã thêm hương thơm và vị hấp dẫn...', image: img2},
        {title: '9 loại đậu bổ dưỡng nên dùng', content: 'Đậu lăng, đậu nành, đậu phộng, đậu Hà Lan giàu chất xơ, protein cùng nhiều vitamin và khoáng chất giúp giảm lượng đường trong máu, tốt cho tim. Nên uống 1 ly hằng ngày để tốt cho sức khỏe...', image: img3}
    ])
</script>