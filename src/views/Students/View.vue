<template>
    <div>
        <div class="card">
            <div class="card-header">
                <h4>Student <RouterLink to="/student/create" class="btn btn-primary float-end">Add Student</RouterLink> </h4>
            </div>
            <div class="card-body">
                <table class="table table-bordered">
                    <thead>
                        <tr>
                            <th>ID</th>
                            <th>Name</th>
                            <th>Course</th>
                            <th>Email</th>
                            <th>Phone</th>
                            <th>Created At</th>
                            <th>Action</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td></td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'students',
    data(){
        return {
            student: []
        }
    },
    mounted() {
        console.log('I am here');
    }
}
</script>