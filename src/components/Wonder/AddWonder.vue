<template>
    <div class="container mt-4">
        <div class="row">

            <div class="col-md-5 mb-1 mx-auto">
                <div class="card shadow">
                    <div class="card-header p-0">
                        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/bf/Bird_Diversity_2013.png/450px-Bird_Diversity_2013.png" class="card-img-top" alt="wonders">
                    </div>
                </div>
            </div>

            <div class="col-md-6 mx-auto">
                <div class="card shadow">
                    <div class="card-header bg-primary">
                        <span class="text-white fs-5">
                            ลงทะเบียนนกที่สวยที่สุดในโลก
                        </span>
                    </div>
                    <div class="card-body text-success">
                        <form @submit.prevent="addWonder">
                            <div class="mb-1">
                                <label for="">ชื่อนกที่สวยที่สุดในโลก</label>
                                <input type="text" class="form-control" v-model="wonderState.name" />
                            </div>
                            <div class="mb-1">
                                <label for="">ตำแหน่ง ที่อยู่ นกที่สวยที่สุดในโลก</label>
                                <input type="text" class="form-control" v-model="wonderState.label" />
                            </div>
                            <div class="mb-1">
                                <label for="">ลิงค์ภาพนกที่สวยที่สุดในโลก</label>
                                <input type="text" class="form-control" v-model="wonderState.imageUrl" />
                            </div>

                            <div class="mb-1">

                                <button type="submit" class="btn btn-primary text-white shadow">
                                    ลงทะเบียนนกที่สวยที่สุดในโลก
                                </button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>

<script setup>
import axios from 'axios'
import { reactive } from 'vue';
import { useRouter } from 'vue-router';

const wonderState = reactive({
    name: '',
    location: '',
    imageUrl:''
})

const router = useRouter()

const addWonder = async () => {
    await axios.post(`https://json-server-vue3-d109.onrender.com/wonders`,wonderState)
        .then(() => {
            console.log(wonderState)
            router.push({name:'wonders'})
        })
    alert('ลงทะเบียนนกที่สวยที่สุดในโลก เรียบร้อยแล้ว')
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Sarabun&display=swap');

.container {
    font-family: 'Sarabun', sans-serif;

}

.form-label {
    color: rgb(18, 229, 102);
}
</style>