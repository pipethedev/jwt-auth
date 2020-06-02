<template>
<div>
    <form @submit.prevent="submit">
        <div class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4 flex flex-col">
            <div class="mb-4">
              <label class="block text-grey-darker text-sm font-bold mb-2" for="username">
                Email Address
              </label>
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-grey-darker" id="email" type="text" placeholder="Username" v-model="form.email">
            </div>
            <div class="mb-6">
              <label class="block text-grey-darker text-sm font-bold mb-2" for="password">
                Password
              </label>
              <input class="shadow appearance-none border border-red rounded w-full py-2 px-3 text-grey-darker mb-3" id="password" type="password" placeholder="******************" v-model="form.password">
              <p class="text-red text-xs italic">Please choose a password.</p>
            </div>
            <div class="flex items-center justify-between">
              <button style="background: blue;" class="bg-blue hover:bg-blue-dark text-white font-bold py-2 px-4 rounded" type="submit">
                Sign In
              </button>
              <a class="inline-block align-baseline font-bold text-sm text-blue hover:text-blue-darker" href="#">
                Forgot Password?
              </a>
            </div>
        </div>
    </form>
</div>

</template>
<style scoped>
    @import url('https://unpkg.com/tailwindcss@^1.0/dist/tailwind.min.css');
</style>
<script>
import { mapActions } from 'vuex'

export default {
  name: 'sign-in',
  components: {
    //
  },
  data(){
    return {
        form: {
            email : '',
            password : '',
        }
    }
  },
  methods: {
    ...mapActions({
        signIn: 'auth/signIn'
    }),
    submit(){
        this.signIn(this.form).then(() => {
          this.$router.replace({
            name: 'dashboard'
          })
        }).catch(() => {
          console.log('failed')
        })
    }
  }
}
</script>
