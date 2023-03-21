<template>
    <form>
        <div>
            <div class="mb-5">
                <label for="small-input" class="text-[#3f7fbf] block mb-2 text-sm font-medium  dark:text-white">Mã sinh
                    viên</label>
                <input v-model="newStudent.masv" type="text" id="small-input"
                    class="block w-full p-2  border border-gray-300 rounded-lg bg-gray-50 sm:text-xs focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
            </div>
            <div class="mb-5">
                <label for="small-input" class="text-[#3f7fbf] block mb-2 text-sm font-medium  dark:text-white">Tên sinh
                    viên</label>
                <input v-model="newStudent.tensv" type="text" id="small-input"
                    class="block w-full p-2  border border-gray-300 rounded-lg bg-gray-50 sm:text-xs focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
            </div>
            <div class="mb-5">
                <label for="small-input" class="text-[#3f7fbf] block mb-2 text-sm font-medium  dark:text-white">Ngày
                    sinh</label>
                <input v-model="newStudent.ngaysinh" type="date" id="small-input"
                    class="block w-full p-2  border border-gray-300 rounded-lg bg-gray-50 sm:text-xs focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
            </div>
            <div class="mb-5">
                <label for="small-input" class="text-[#3f7fbf] block mb-2 text-sm font-medium  dark:text-white">Giới
                    tính</label>
                <input v-model="newStudent.gioitinh" type="text" id="small-input"
                    class="block w-full p-2  border border-gray-300 rounded-lg bg-gray-50 sm:text-xs focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
            </div>
            <div class="mb-5">
                <label for="small-input" class="text-[#3f7fbf] block mb-2 text-sm font-medium  dark:text-white">Mã
                    khoa</label>
                <input v-model="newStudent.makhoa" type="text" id="small-input"
                    class="block w-full p-2  border border-gray-300 rounded-lg bg-gray-50 sm:text-xs focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
            </div>
            <div class="mb-5">
                <label for="small-input" class="text-[#3f7fbf] block mb-2 text-sm font-medium  dark:text-white">Tên
                    khoa</label>
                <input v-model="newStudent.tenkhoa" type="text" id="small-input"
                    class="block w-full p-2  border border-gray-300 rounded bg-gray-50 sm:text-xs focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
            </div>
            <div class="float-right">
                <button v-on:click.prevent="addStudent"
                    class="bg-transparent hover:bg-blue-500 text-[#3f7fbf] font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded">
                    Thêm sinh viên
                </button>
            </div>
        </div>
    </form>
</template>

<script>
export default {
    data() {
        return {
            newStudent: { masv: '', tensv: '', ngaysinh: '', gioitinh: '', makhoa: '', tenkhoa: '' }
        }
    },

    methods: {
        addStudent() {
            this.$emit('add', this.newStudent)
            this.newStudent = { masv: '', tensv: '', ngaysinh: '', gioitinh: '', makhoa: '', tenkhoa: '' }
        }
    }

}
</script>
