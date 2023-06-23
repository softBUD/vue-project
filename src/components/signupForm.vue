<template>
  <div class="flex pt-20 justify-content items-center flex-col">
    <div>
      <h2 class="text-2xl font-bold">Sign in your Account</h2>
    </div>
    <form class="pt-10 flex flex-col">
      <label for="email" class="mr-2">Email</label>
      <input
        v-model="email"
        type="text"
        placeholder="이메일을 입력해주세요"
        class="border-b-slate-500 border-solid border-b-2 mt-3"
      />

      <label for="password" class="mt-3">password</label>
      <input
        v-model="password"
        type="text"
        placeholder="비밀번호"
        class="border-b-slate-500 border-solid border-b-2 mt-3"
      />
      <label for="role" class="mt-3">포지션</label>
      <select name="role" id="role" v-model="role" class="mt-3">
        <option value="designer">designer</option>
        <option value="developer">developer</option>
        <option value="operator">operator</option>
      </select>

      <label for="skills" class="mt-3">스킬</label>
      <input
        type="text"
        v-model="tempSkill"
        @keyup="addSkill"
        class="border-b-slate-500 border-solid border-b-2 mt-3"
      />
    </form>
  </div>
  <div>{{ email }}</div>
  <div>{{ password }}</div>
  <div>{{ `제 스킬은 :  ${skills}` }}</div>
</template>
<script>
export default {
  name: 'SignupForm',
  data() {
    return {
      email: '',
      password: '',
      role: '',
      tempSkill: '',
      skills: []
    }
  },
  watch: {},
  methods: {
    addSkill($event) {
      if ($event.key === ',' && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill.slice(0, -1))
          this.tempSkill = ''
        }
      }
    }
  }
}
</script>
<style></style>
