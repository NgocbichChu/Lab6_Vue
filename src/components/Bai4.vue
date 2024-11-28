<template>
    <div class="container">
        <div class="row">
            <form @submit.prevent="SubmitForm" class="col-sm-4">
                <h4 class="text-center">Thêm Sinh viên</h4>
                <div class="mb-3 mt-3">
                    <label for="name">Họ tên SV</label>
                    <input type="text" class="form-control" id="name" v-model="student.name" required/>
                </div>

                <div class="mb-3">
                    <label for="dob">Ngày sinh</label>
                    <input type="date" class="form-control" id="dob" v-model="student.dob" required/>
                </div>

                <div class="mb-3">
                    <label for="score">Điểm</label>
                    <input type="number" min="0" max="10" class="form-control" id="score" v-model="student.score" required/>
                </div>

                <button type="submit" class="btn btn-success">{{ isEditing ? 'Cập nhật' : 'Thêm' }}</button>
            </form>

            <div class="col-sm-7">
                <h4 class="text-center">Danh sách Sinh viên</h4>
                <table class="table table-bordered">
                    <thead>
                        <tr class="text-center">
                            <th>Họ tên</th>
                            <th>Ngày sinh</th>
                            <th>Điểm</th>
                            <th colspan="2">Trạng thái</th>
                            
                        </tr>
                    </thead>

                    <tbody>
                        <tr v-for="(stu, index) in students" :key="index">
                            <td class="col-2">{{ stu.name }}</td>
                            <td class="col-2">{{ stu.dob }}</td>
                            <td class="col-1">{{ stu.score }}</td>
                            <td class="text-center col-1">
                                <button class="btn btn-warning" @click="editStudent(index)">Sửa</button>
                            </td>
                            <td class="text-center col-1">
                                <button class="btn btn-danger" @click="deleteStudent(index)">Xóa</button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script setup>
    import { ref } from 'vue';
    
    const students = ref ([
        { name: 'Chu Thị Ngọc Bích', dob: '2005-01-26', score: 8 },
        { name: 'Lê Thị Thanh Nguyên', dob: '2006-06-17', score: 9 }
    ])

    const student = ref ({
        name: '',
        dob: '',
        score: null
    })

    let isEditing = ref(false)
    let editingIndex = ref(null)

    function SubmitForm() {
        if (isEditing.value) {
            students.value[editingIndex.value] = { ...student.value }
            isEditing.value = false
            editingIndex.value = null
        } else {
            students.value.push({ ...student.value })
        }
        resetForm()
    }

    function editStudent(index) {
        student.value = { ...students.value[index] }
        isEditing.value = true
        editingIndex.value = index
    }

    function deleteStudent(index) {
        students.value.splice(index, 1)
    }

    function resetForm() {
        student.value = {
            name: '',
            dob: '',
            score: null
        }
    }
</script>