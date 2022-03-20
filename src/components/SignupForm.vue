<template>

  <form action="" class="max-w-md my-4 mx-auto bg-white p-10 rounded-md">
    <h1 class="text-2xl font-semibold py-3 px-2 text-center uppercase text-blue-500"
    >Sign Up</h1>
    <div class="mb-4">
      <label for="email" class="text-gray-400 inline-block text-xs uppercase font-semibold tracking-wide py-3"
      >Email:</label>
      <input type="email" name="email" id="email" placeholder="email@example.com" class="block py-1 px-2 w-full box-border
      border-b-2 border-gray-300 rounded-md text-gray-600 focus:outline-gray-300 
      mb-2"
      required
      v-model="email"/>
      <p class="text-red-500 text-xs italic">Please enter a valid email.</p>

    </div>
    <div class="mb-4">
      <label for="password" class="text-gray-400 inline-block text-xs uppercase font-semibold tracking-wide py-3"
      >Password:</label>
      <input type="password" name="password" id="password" class="block py-1 px-2 w-full box-border
      border-b-2 border-gray-300 rounded-md text-gray-400 focus:outline-gray-300 
       mb-2"
      required
      v-model="password"/>
      <p class="text-red-500 text-xs italic">Please choose a password.</p>
    </div>
    <div class="mb-4">
      <label for="role" class="text-gray-400 inline-block text-xs uppercase font-semibold tracking-wide py-3"
      >Role:</label>
      <select name="role" id="role" class="block py-1 px-2 w-full box-border
      border-b-2 border-gray-300 rounded-md text-gray-400 focus:outline-gray-300 
     mb-2"
      required
      v-model="role">
        <option value="developer">Web Developer</option>
        <option value="designer">Web Designer</option>
        <option value="project manager">Project Manager</option>
      </select>
      <p class="text-red-500 text-xs italic">This field is required.</p>
    </div>
    <div class="mb-4">
      <label for="skills" class="text-gray-400 inline-block text-xs uppercase font-semibold tracking-wide py-3"
      >Skills:</label>
      <p class="text-xs text-gray-500">Separate skills with a comma</p>
      <input type="text" name="skills" id="skills" 
      class="block py-1 px-2 w-full box-border
      border-b-2 border-gray-300 rounded-md text-gray-600 focus:outline-gray-300 
      mb-2"
      required
      v-model="tempSkill"
      @keyup="addSkill"/>
      <div class="flex flex-wrap">
      <div v-for="skill in skills" :key="skill" class="bg-emerald-200 rounded-full py-1 px-3 m-1 text-xs text-gray-600 uppercase font-semibold cursor-pointer" >
      <span @click.prevent="deleteSkill(skill)">{{skill}}</span>
      </div>
      </div>

    </div>

    <div class="mb-4">
      <p class="text-gray-400 block text-xs
      font-semibold tracking-wide py-3">What is the best time to call? (select all that apply)</p>
      <input type="checkbox" name="contactTime" class="inline-block
     border-gray-300 rounded-md text-gray-400 focus:outline-gray-300 
      focus:bg-blue-100
      relative top-1"
      v-model="contactTime"
      value="morning"/>
      <label for="contactTime" class="text-gray-400 inline-block text-xs uppercase 
      font-semibold tracking-wide py-3 px-2"
      >Morning</label>
      <input type="checkbox" name="contactTime" class="inline-block
     border-gray-300 rounded-md text-gray-400 focus:outline-gray-300 
      focus:bg-blue-100
      relative top-1"
      v-model="contactTime"
      value="afternoon"/>
      <label for="contactTime" class="text-gray-400 inline-block text-xs uppercase 
      font-semibold tracking-wide py-3 px-2"
      >Afternoon</label>
      <input type="checkbox" name="contactTime" class="inline-block
     border-gray-300 rounded-md text-gray-400 focus:outline-gray-300 
      focus:bg-blue-100
      relative top-1"
      v-model="contactTime"
      value="evening"/>
      <label for="contactTime" class="text-gray-400 inline-block text-xs uppercase 
      font-semibold tracking-wide py-3 px-2"
      >Evening</label>
    </div>
    <div class="mb-4">
      <input type="checkbox" name="terms" id="terms" class="inline-block
     border-gray-300 rounded-md text-gray-400 focus:outline-gray-300 
      focus:bg-blue-100
      relative top-1"
      required
      v-model="terms"/>
      <label for="terms" class="text-gray-400 inline-block text-xs uppercase font-semibold tracking-wide py-3 px-2"
      >Please accept the terms and conditions.</label>
      
      <p class="text-red-500 text-xs italic">Please accept the terms.</p>
    </div>
    <div class="flex items-center justify-between">
      <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
        Sign In
      </button>
      <a class="inline-block align-baseline font-bold text-sm text-blue-500 hover:text-blue-800" href="#">
        Forgot Password?
      </a>
    </div>
  </form>
  <div class="max-w-md mx-auto">
    <p>Email: {{email}}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>Terms Accepted: {{terms}}</p>
    <p>Best time: {{contactTime}}</p>
    <p>Skills: {{ skills }}</p>

  </div>

</template>

<script>
export default {
  name: 'SignupForm',
  data() {
    return {
      email: '',
      password: '',
      role: 'developer',
      terms: false,
      contactTime: [],
      tempSkill: '',
      skills: []
    }
  },
  methods: {
    addSkill(e) {
      if (e.key === ',' && this.tempSkill) {
        // skill cannot be entered twice
        if(!this.skills.includes(this.tempSkill)) {
          // make lowercase and strip comma
          this.skills.push(this.tempSkill.toLowerCase().slice(0,-1))
          
        }
        this.tempSkill = ''
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter((item) => {
        // remove item if it returns false (the skill that was passed in)
        return skill !== item;
      })
    }
  }
}
</script>
