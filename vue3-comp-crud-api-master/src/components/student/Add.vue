<script setup>
import { reactive } from "vue";
import { RouterLink } from "vue-router";
import useStudent from "../../composables/studentApi";
const { studentData, error, statusCode, createStudent } = useStudent();
const formData = reactive({
  stuname: "",
  email: "",
});
const handleAddStudentForm = async () => {
  await createStudent(formData);
  if (statusCode.value === 201) {
    document.getElementById("AddStudentForm").reset();
  }
};
</script>

<template>
  <div class="shadow-md pb-6">
    <div class="bg-indigo-600 p-4">
      <h1 class="text-3xl font-bold text-center text-white">Add Client</h1>
    </div>

    <form
      @submit.prevent="handleAddStudentForm"
      class="w-full"
      id="AddStudentForm"
    >
      <div class="flex items-center m-6">
        <div class="w-1/5">
          <label class="font-medium" for="stuname"> FirstName : </label>
        </div>
        <div class="w-4/5">
          <input
            type="text"
            id="stuname"
            v-model.trim="formData.stuname"
            class="border-2 border-gray-200 w-full py-2 px-4"
            placeholder="write your First Name"
            required
          />
        </div>
      </div>

      <div class="flex items-center m-6">
        <div class="w-1/5">
          <label class="font-medium" for="stuname"> LastName : </label>
        </div>
        <div class="w-4/5">
          <input
            type="text"
            id="stuname"
            v-model.trim="formData.stuname"
            class="border-2 border-gray-200 w-full py-2 px-4"
            placeholder="write your Last name"
            required
          />
        </div>
      </div>

      <div class="flex items-center m-6">
        <div class="w-1/5">
          <label class="font-medium" for="email"> Email : </label>
        </div>
        <div class="w-4/5">
          <input
            type="email"
            id="email"
            v-model.trim="formData.email"
            class="border-2 border-gray-200 w-full py-2 px-4"
            placeholder="write your email"
            required
          />
        </div>
      </div>

      <div class="flex items-center m-6">
        <div class="w-1/5">
          <label class="font-medium" for="email"> phoneno: </label>
        </div>
        <div class="w-4/5">
          <input
            type="phoneno"
            id="phoneno"
            v-model.trim="formData.phoneno"
            class="border-2 border-gray-200 w-full py-2 px-4"
            placeholder="write your phoneno"
            required
          />
        </div>
      </div>
  
      <div class="flex items-center m-6">
        <div class="w-1/5">
          <label class="font-medium" for="gender"> Customercode: </label>
        </div>
        <div class="w-4/5">
          <input
            type="Countrycode"
            id="Countrycode"
            v-model.trim="formData.Countrycode"
            class="border-2 border-gray-200 w-full py-2 px-4"
            placeholder="write your Countrycode"
            required
          />
        </div>
      </div>

      <div class="flex items-center m-6">
        <div class="w-1/5">
          <label class="font-medium" for="gender"> Gender: </label>
        </div>
        <div class="w-4/5">
          <input
            type="phoneno"
            id="phoneno"
            v-model.trim="formData.gender"
            class="border-2 border-gray-200 w-full py-2 px-4"
            placeholder="write your gender"
            required
          />
        </div>
      </div>

      <div class="flex items-center m-6">
        <div class="w-1/5">
          <label class="font-medium" for="balance"> Balance </label>
        </div>
        <div class="w-4/5">
          <input
            type="balance"
            id="balance"
            v-model.trim="formData.balance"
            class="border-2 border-gray-200 w-full py-2 px-4"
            placeholder="write your balance"
            required
          />
        </div>
      </div>


      <div class="m-8 flex justify-center">
        <button
          type="submit"
          class="bg-purple-700 text-white font-medium py-2 rounded-md px-6 hover:bg-purple-800 mr-6"
        >
          Add
        </button>

        <RouterLink :to="{ name: 'list' }">
          <button
            type="button"
            class="bg-emerald-700 text-white font-medium p-2 rounded-md hover:bg-emerald-800"
          >
            Back to Home
          </button>
        </RouterLink>
      </div>
    </form>
    <div
      class="p-4 mb-4 text-sm text-red-700 bg-red-100 rounded-lg font-medium"
      role="alert"
      v-if="error"
    >
      Oops! Error encountered: {{ error.message }}
    </div>
    <div
      class="p-4 mb-4 text-sm text-red-700 bg-red-100 rounded-lg font-medium"
      role="alert"
      v-if="statusCode === 201"
    >
      lClient Added Successfully
    </div>
  </div>
</template>

<style scoped></style>
