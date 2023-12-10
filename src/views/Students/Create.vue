<template>
    <div class="container mt-5">
        <div class="card">
            <div class="card-header">
                <h4>Add Students</h4>
            </div>
            <div class="card-body">
                <ul class="alert alert-warning" v-if="Object.keys(this.errorList).length > 0">
                    <li class="mb-0 ms-3" v-for="(error, index) in this.errorList" :key="index">
                        {{ error[0] }}
                    </li>
                </ul>
                <div class="mb-3">
                    <label for="name">Name</label>
                    <input type="text" v-model="model.student.name" class="form-control">
                </div>
                <div class="mb-3">
                    <label for="name">Course</label>
                    <input type="text" v-model="model.student.course" class="form-control">
                </div>
                <div class="mb-3">
                    <label for="name">Email</label>
                    <input type="text" v-model="model.student.email" class="form-control">
                </div>
                <div class="mb-3">
                    <label for="name">Phone</label>
                    <input type="text" v-model="model.student.phone" class="form-control">
                </div>
                <div class="mb-3">
                    <button type="button" class="btn btn-primary" @click="saveStudent">Save</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name: 'StudentCreate',
    data() {

        return {
            errorList: '',
            model: {
                student: {
                    name: '',
                    course: '',
                    email: '',
                    phone: ''
                }
            }
        }
    },
    methods: {
        saveStudent() {
            let mythis = this;
            axios.post('http://127.0.0.1:8000/api/students', this.model.student)
                .then(res => {
                    console.log(res.data);
                    alert(res.data.message);

                    this.model.student = {
                        name: '',
                        course: '',
                        email: '',
                        phone: ''
                    }
                    this.errorList = '';
                })
                .catch(function (error) {
                    if (error.response) {
                        // The request was made and the server responded with a status code
                        // that falls out of the range of 2xx
                        if(error.response.status){
                            mythis.errorList = error.response.data.errors;
                        }
                        console.log(error.response.data);
                        console.log(error.response.status);
                        console.log(error.response.headers);
                    } else if (error.request) {
                        // The request was made but no response was received
                        // `error.request` is an instance of XMLHttpRequest in the browser and an instance of
                        // http.ClientRequest in node.js
                        console.log(error.request);
                    } else {
                        // Something happened in setting up the request that triggered an Error
                        console.log('Error', error.message);
                    }
                    console.log(error.config);
                });
        }
    }
}
</script>
