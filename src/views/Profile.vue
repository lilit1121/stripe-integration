<template>
    <form class="page">
      <div class="responsive-d">
        <div class="d-flex flex-column responsive-w">
            <label class="label mb-2" for="firstname">First Name</label>
            <input type="text" id="firstname" v-model="user.firstname" @keypress="isLetter($event)">
            <p class="text-danger error" v-if="!$v.user.firstname.required">First Name Is Required</p>
            <p class="text-danger error" v-if="!$v.user.firstname.minLength">First Name Can Consist More Than 1 Letter</p>
        </div>
        <div class="d-flex flex-column responsive-w mt-1rem">
            <label class="label mb-2" for="lastname">Last Name</label>
            <input type="text" id="lastname" v-model="user.lastname" @keypress="isLetter($event)">
            <p class="text-danger error" v-if="!$v.user.lastname.required">Last Name Is Required</p>
            <p class="text-danger error" v-if="!$v.user.lastname.minLength">Last Name Can Consist More Than 1 Letter</p>
        </div>
      </div>
      <div class="responsive-d mt-3">
        <div class="d-flex flex-column responsive-w">
            <label class="label mb-2" for="female">Gender</label>
            <div class="d-flex">
                <div class="mr-3 d-flex align-items-center">
                    <label class="mb-0 mr-2 cursor-pointer" for="female">Female</label>
                    <input id="female" type="radio" name="gender" value="female" v-model="user.gender">
                </div>
                <div class="d-flex align-items-center">
                    <label class="mb-0 mr-2 cursor-pointer" for="male">Male</label>
                    <input id="male" type="radio" name="gender" value="male" v-model="user.gender"> 
                </div>  
            </div>
        </div>
        <div class="d-flex flex-column responsive-w mt-1rem">
            <label class="label mb-2" for="dob">Date Of Birth</label>
            <input id="dob" type="date" v-model="user.dob" :max="disable()">
            <p class="text-danger error" v-if="!$v.user.dob.required">Date Of Birth Is Required</p>
        </div>
      </div>
      <div class="d-flex justify-content-end mt-5">
            <b-button class="responsive-w blue-btn" variant="info" @click="saveUserInfo">Submit</b-button>
      </div>
    </form>
</template>

<style scoped>
    .responsive-d{
        display: flex;
        justify-content: space-between;
    }
    .responsive-w{
        width: calc(50% - 10px);
    }
    .label{
        color: #484d4e;
        font-weight: 600;
    }
    @media only screen and (max-width: 600px) {
        .responsive-w{
            width: 100%;
        }
        .responsive-d{
            display: inherit;
        }
        .mt-1rem{
            margin-top: 1rem;
        }
    }
</style>

<script>
import { required, minLength } from 'vuelidate/lib/validators'
export default {
    data(){
        return{
            user: {
                firstname: '',
                lastname: '',
                gender: 'female',
                dob: null
            }
        }
    },
    methods: {
        disable(){
            let today = new Date();
            let dd = today.getDate();
            let mm = today.getMonth() + 1;
            let yyyy = today.getFullYear();

            if (dd < 10) {
            dd = '0' + dd;
            }

            if (mm < 10) {
            mm = '0' + mm;
            } 
                
            today = yyyy + '-' + mm + '-' + dd;
            return today
        },
        saveUserInfo(){
            this.$v.user.$touch()
            if (!this.$v.user.$anyError) {
                localStorage.setItem('user', JSON.stringify(this.user));
            }
        },
        isLetter(e) {
            let char = String.fromCharCode(e.keyCode);
            if(/^[A-Za-z]+$/.test(char)) return true;
            else e.preventDefault();
        }
    },
    validations: {
        user: {
            firstname: {required, minLength: minLength(2)},
            lastname: {required, minLength: minLength(2)},
            dob: {required}
        }
    }
}
</script>
