<template>
  <div>
    <div class="container">
      <h1 class="font-bold text-[3em] text-center text-[#3f7fbf]">Quản lý sinh viên</h1>
      <div class="mt-8">
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
      showEditForm: false,
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
    },
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



<!-- <template>
  <div>
    <div class="container">
      <h1 class="font-bold text-[3em] text-center text-[#3f7fbf]">Quản lý sinh viên</h1>
      <div class="mt-8">
        <div class="float-left w-[35%] p-5 box-border shadow-lg">
          <label for="table-search" class="sr-only">Tìm kiếm</label>
          <div class="flex items-center">
            <div class="relative mt-1 mb-3">
              <div class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none">
                <svg class="w-5 h-5 text-gray-500 dark:text-gray-400" aria-hidden="true" fill="currentColor"
                  viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
                  <path fill-rule="evenodd"
                    d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
                    clip-rule="evenodd"></path>
                </svg>
              </div>
              <input v-model="searchText" type="text" id="table-search"
                class="block p-2 pl-10 text-sm text-gray-900 border border-gray-300 rounded w-80 bg-gray-50 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                placeholder="Tìm kiếm...">


            </div>
            <div class="flex items-center m-auto mb-3">
              <button
                class="
                              bg-transparent hover:bg-blue-500 text-[#3f7fbf] font-semibold hover:text-white py-[6px] px-4 border border-blue-500 hover:border-transparent rounded">
                Tìm kiếm
              </button>
            </div>
          </div>
          <add-student-form v-on:add="addStudent"></add-student-form>
        </div>
        <div>
          <div v-if="filteredStudents.length === 0" class="text-center mt-5">Không có kết quả phù hợp.</div>
          <student-list :students="filteredStudents" v-on:edit="editStudent" v-on:delete="deleteStudent"></student-list>
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
      showEditForm: false,
      searchText: ''
    }
  },

  computed: {
    filteredStudents() {
      return this.students.filter(student => {
        const tensv = student.tensv.toLowerCase()
        const searchText = this.searchText.toLowerCase()
        return tensv.includes(searchText)
      })
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
      if (confirm('Bạn có chắc chắn muốn xoá sinh viên này?')) {
        this.students.splice(index, 1)
        localStorage.setItem('students', JSON.stringify(this.students))
        toast.success('Xoá sinh viên thành công!');
      }
    },
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
</style> -->
