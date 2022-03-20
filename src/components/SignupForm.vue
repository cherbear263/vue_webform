<template>

  <form action="" class="max-w-md my-4 mx-auto bg-white p-10 rounded-md">
    <h1 class="text-2xl font-semibold py-3 px-2 text-center uppercase text-blue-500"
    >Sign Up</h1>
    <label for="email" class="text-gray-400 inline-block text-xs uppercase font-semibold tracking-wide py-3 px-2"
    >Email:</label>
    <input type="email" name="email" id="email" placeholder="email@example.com" class="block py-1 px-2 w-full box-border
    border-b-2 border-gray-300 rounded-md text-gray-600 focus:outline-gray-300 
    focus:bg-blue-100 mb-2"
    required
    v-model="email"/>
    <label for="password" class="text-gray-400 inline-block text-xs uppercase font-semibold tracking-wide py-3 px-2"
    >Password:</label>
    <input type="password" name="password" id="password" class="block py-1 px-2 w-full box-border
    border-b-2 border-gray-300 rounded-md text-gray-400 focus:outline-gray-300 
    focus:bg-blue-100 mb-2"
    required
    v-model="password"/>
  </form>
  <div class="max-w-md mx-auto">
      <p>Email: {{email}}</p>
  <p>Password: {{ password }}</p>
  </div>

</template>

<script>
export default {
  name: 'SignupForm',
  data() {
    return {
      email: 'mario@mariobros.com',
      password: 'princessPeach',
    }
  }
}
</script>
