<template>
    <div class="relative overflow-x-auto shadow-md">
        <div class="pb-4 bg-white dark:bg-gray-900 flex items-center justify-center gap-5">
            <label for="table-search" class="sr-only">Tìm kiếm</label>
            <div class="relative mt-1">
                <div class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none">
                    <svg class="w-5 h-5 text-gray-500 dark:text-gray-400" aria-hidden="true" fill="currentColor"
                        viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
                        <path fill-rule="evenodd"
                            d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
                            clip-rule="evenodd"></path>
                    </svg>
                </div>
                <input type="text" id="table-search"
                    class="block p-2 pl-10 text-sm text-gray-900 border border-gray-300 rounded w-80 bg-gray-50 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                    placeholder="Tìm kiếm...">
            </div>
            <div class="flex items-center">
                <button
                    class="bg-transparent hover:bg-blue-500 text-[#3f7fbf] font-semibold hover:text-white py-[6px] px-4 border border-blue-500 hover:border-transparent rounded">
                    Tìm kiếm
                </button>
            </div>
        </div>
        <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
            <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                <tr>
                    <th scope="col" class="p-4">
                        <div class="flex items-center">
                            <input id="checkbox-all-search" type="checkbox"
                                class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 dark:focus:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600">
                            <label for="checkbox-all-search" class="sr-only">checkbox</label>
                        </div>
                    </th>
                    <th scope="col" class="px-6 py-3 text-[#3f7fbf]">
                        Mã sinh viên
                    </th>
                    <th scope="col" class="px-6 py-3 text-[#3f7fbf]">
                        Tên sinh viên
                    </th>
                    <th scope="col" class="px-6 py-3 text-[#3f7fbf]">
                        Ngày sinh
                    </th>
                    <th scope="col" class="px-6 py-3 text-[#3f7fbf]">
                        Giới tính
                    </th>
                    <th scope="col" class="px-6 py-3 text-[#3f7fbf]">
                        Mã khoa
                    </th>
                    <th scope="col" class="px-6 py-3 text-[#3f7fbf]">
                        Tên khoa
                    </th>
                    <th scope="col" class="px-6 py-3 text-[#3f7fbf]">
                        Chức năng
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-600">
                    <td class="w-4 p-4">
                        <div class="flex items-center">
                            <input id="checkbox-table-search-1" type="checkbox"
                                class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 dark:focus:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600">
                            <label for="checkbox-table-search-1" class="sr-only">checkbox</label>
                        </div>
                    </td>
                    <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                        26565
                    </th>
                    <td class="px-6 py-4">
                        Thiều Trần Cương
                    </td>
                    <td class="px-6 py-4">
                        2002-06-16
                    </td>
                    <td class="px-6 py-4">
                        Nam
                    </td>
                    <td class="px-6 py-4">
                        CS
                    </td>
                    <td class="px-6 py-4">
                        CNTT
                    </td>
                    <td class="px-6 py-4">
                        <a href="#" class="font-medium text-blue-600 dark:text-blue-500 hover:underline">Sửa</a>/
                        <a href="#" class="font-medium text-red-600 dark:text-blue-500 hover:underline">Xoá</a>
                    </td>
                </tr>
                <tr v-for="(student, index) in students" :key="index"
                    class="bg-white border-b dark:bg-gray-800 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-600">
                    <td class="w-4 p-4">
                        <div class="flex items-center">
                            <input id="checkbox-table-search-1" type="checkbox"
                                class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 dark:focus:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600">
                            <label for="checkbox-table-search-1" class="sr-only">checkbox</label>
                        </div>
                    </td>
                    <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                        {{ student.masv }}
                    </th>
                    <td class="px-6 py-4">
                        {{ student.tensv }}
                    </td>
                    <td class="px-6 py-4">
                        {{ student.ngaysinh }}
                    </td>
                    <td class="px-6 py-4">
                        {{ student.gioitinh }}
                    </td>
                    <td class="px-6 py-4">
                        {{ student.makhoa }}
                    </td>
                    <td class="px-6 py-4">
                        {{ student.tenkhoa }}
                    </td>
                    <td class="px-6 py-4">
                        <a v-on:click.prevent="editStudent(index)" href="#"
                            class="font-medium text-blue-600 dark:text-blue-500 hover:underline">Sửa</a>/
                        <a v-on:click.prevent="deleteStudent(index)" href="#"
                            class="font-medium text-red-600 dark:text-blue-500 hover:underline">Xoá</a>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import { toast } from 'vue3-toastify';
import 'vue3-toastify/dist/index.css';
export default {
    props: ['students'],
    methods: {
        editStudent(index) {
            this.$emit('edit', index)
        },
        deleteStudent(index) {
            this.$emit('delete', index)
            toast.success('Xoá sinh viên thành công!');
        },
    }
}
</script>

<style></style>