<template>
  <div>
    <div class="container">
      <h1 class="font-bold text-[3em] text-center text-[#3f7fbf]">Quản lý sinh viên</h1>
      <div class="mt-[50px]">
        <div class="float-left w-[35%] p-5 box-border shadow-lg">
          <add-student-form v-on:add="addStudent"></add-student-form>
        </div>
        <div>
          <student-list :students="students" v-on:edit="editStudent" v-on:delete="deleteStudent"></student-list>
          <div class="overlay" v-if="showEditForm">
            <edit-student-form :selected-student="selectedStudent" v-on:save="saveStudent"
              v-on:cancel="cancelEdit"></edit-student-form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import AddStudentForm from './components/AddStudentForm.vue';
import StudentList from './components/StudentList.vue';
import EditStudentForm from './components/EditStudentForm.vue';
export default {

  data() {
    return {
      students: JSON.parse(localStorage.getItem('students') || '[]'),
      selectedStudent: null,
      showEditForm: false
    }
  },

  methods: {
    addStudent(newStudent) {
      this.students.push(newStudent)
      localStorage.setItem('students', JSON.stringify(this.students))
    },
    editStudent(index) {
      this.selectedStudent = { ...this.students[index] }
      this.showEditForm = true
    },
    saveStudent(updatedStudent) {
      const index = this.students.findIndex(student => student.name === updatedStudent.name && student.age === updatedStudent.age)
      if (index !== -1) {
        this.students[index] = updatedStudent
        localStorage.setItem('students', JSON.stringify(this.students))
        this.selectedStudent = null
        this.showEditForm = false
      }
    },
    cancelEdit() {
      this.selectedStudent = null
      this.showEditForm = false
    },
    deleteStudent(index) {
      if (confirm('Bạn có chắc muốn xoá chứ?')) {
        this.students.splice(index, 1)
        localStorage.setItem('students', JSON.stringify(this.students))
      }
    }
  },

  components: { AddStudentForm, StudentList, EditStudentForm }
}
</script>
<style>
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 999;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
