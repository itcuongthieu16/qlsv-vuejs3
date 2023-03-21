<template>
    <form>
        <div>
            <div class="mb-5">
                <label for="small-input" class="text-[#3f7fbf] block mb-2 text-sm font-medium  dark:text-white">Mã sinh
                    viên</label>
                <input v-model="selectedStudent.masv" type="text" id="small-input"
                    class="block w-full p-2  border border-gray-300 rounded-lg bg-gray-50 sm:text-xs focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
            </div>
            <div class="mb-5">
                <label for="small-input" class="text-[#3f7fbf] block mb-2 text-sm font-medium  dark:text-white">Tên sinh
                    viên</label>
                <input v-model="selectedStudent.tensv" type="text" id="small-input"
                    class="block w-full p-2  border border-gray-300 rounded-lg bg-gray-50 sm:text-xs focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
            </div>
            <div class="mb-5">
                <label for="small-input" class="text-[#3f7fbf] block mb-2 text-sm font-medium  dark:text-white">Ngày
                    sinh</label>
                <input v-model="selectedStudent.ngaysinh" type="date" id="small-input"
                    class="block w-full p-2  border border-gray-300 rounded-lg bg-gray-50 sm:text-xs focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
            </div>
            <div class="mb-5">
                <label for="small-input" class="text-[#3f7fbf] block mb-2 text-sm font-medium  dark:text-white">Giới
                    tính</label>
                <input v-model="selectedStudent.gioitinh" type="text" id="small-input"
                    class="block w-full p-2  border border-gray-300 rounded-lg bg-gray-50 sm:text-xs focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
            </div>
            <div class="mb-5">
                <label for="small-input" class="text-[#3f7fbf] block mb-2 text-sm font-medium  dark:text-white">Mã
                    khoa</label>
                <input v-model="selectedStudent.makhoa" type="text" id="small-input"
                    class="block w-full p-2  border border-gray-300 rounded-lg bg-gray-50 sm:text-xs focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
            </div>
            <div class="mb-5">
                <label for="small-input" class="text-[#3f7fbf] block mb-2 text-sm font-medium  dark:text-white">Tên
                    khoa</label>
                <input v-model="selectedStudent.tenkhoa" type="text" id="small-input"
                    class="block w-full p-2  border border-gray-300 rounded bg-gray-50 sm:text-xs focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
            </div>
            <div class="float-right">
                <button v-on:click.prevent="saveStudent"
                    class="bg-transparent hover:bg-blue-500 text-[#3f7fbf] font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded">
                    Lưu sinh viên
                </button>
                <button v-on:click.prevent="cancelEdit"
                    class="bg-transparent hover:bg-blue-500 text-[#3f7fbf] font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded">
                    Thoát
                </button>
            </div>
        </div>
    </form>
</template>

<script>
export default {
    props: ['selectedStudent'],
    methods: {
        saveStudent() {
            this.$emit('save', this.selectedStudent)
        },
        cancelEdit() {
            this.$emit('cancel')
        }
    }
}
</script>

<style></style>