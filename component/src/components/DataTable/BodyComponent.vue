<template>
    <div>
    <table class="table table-striped">
        <tbody>
            <tr>
                <th>ID</th>
                <th>Name</th>
                <th>City</th>
            </tr>
            <tr v-for="stu in students" :key="stu.id">
                <td>{{ stu.id }}</td>
                <td>{{ stu.name }}</td>
                <td>{{ stu.city }}</td>
            </tr>
        </tbody>
    </table>
    <p> # of students: {{ students.length }}</p>

    <button class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal">
      Add Student
    </button>
    <button class="btn btn-danger" data-bs-toggle="modal" data-bs-target="#exampleModal2">
      Delete Student
    </button>
    <button class="btn btn-warning" data-bs-toggle="modal" data-bs-target="#exampleModal3">
      Update Student
    </button>

    
    <AddStudent @addNewStudent="addNewStudent" />
    <DelStudent @deleteStudent="deleteStudent"/>
    <UpdateStudent :students="students" @updateStudent="updateStudent" />
  </div>



</template>

<script>
import UpdateStudent from "./UpdateStudent.vue"
import DelStudent from "./DeleteStudent.vue"
import AddStudent from "./AddStudent.vue"
export default{
    components: {
        AddStudent,
        DelStudent,
        UpdateStudent,
    },
    data:()=>({
        students:[]
    }),
    created(){
        this.listData()
    },
    methods:{
        async listData(){
            const response = await fetch('http://localhost:3000/students',{method:"GET",headers:{"Content-type":"application/json"}})
            this.students = await response.json();
            
        },
        async addNewStudent(data){
            let newData={
                name:data.name,
                city:data.city
            }
            await fetch('http://localhost:3000/students',{method:"POST",headers:{"Content-type":"application/json"},body: JSON.stringify(newData)});
            this.listData();
            console.log(data.name)
        },
        async deleteStudent(data){
            await fetch(`http://localhost:3000/students/${data.id}`,{method:"DELETE",headers:{"Content-type":"application/json"}});
            this.listData();
        },
        async updateStudent(data){
            let newData={                
                name:data.name,
                city:data.city
            }
            await fetch(`http://localhost:3000/students/${data.id}`,{method:"PUT",headers:{"Content-type":"application/json"},body: JSON.stringify(newData)});
            this.listData();
        }
        
    }
}   

</script>