<template>
    <div class="page">

        <h3 class="text-center mb-4">
            Đăng nhập hệ thống
        </h3>

        <div class="form-group">
            <label>Tên đăng nhập</label>

            <input
                class="form-control"
                v-model="username"
            >
        </div>

        <div class="form-group">

            <label>Mật khẩu</label>

            <input
                type="password"
                class="form-control"
                v-model="password"
            >
        </div>

        <button
            class="btn btn-primary"
            @click="login"
        >
            Đăng nhập
        </button>

        <p class="text-danger mt-3">
            {{ message }}
        </p>

    </div>
</template>

<script>
import UserService from "@/services/user.service";

export default {

    data() {

        return{

            username:"",
            password:"",
            message:""

        }

    },

    methods:{

        async login(){

            try{

                const result =
                    await UserService.login({

                        username:this.username,
                        password:this.password

                    });

                localStorage.setItem(
                    "login",
                    JSON.stringify(result.user)
                );

                this.$router.push({
                    name:"contactbook"
                });

            }

            catch(error){

                this.message="Sai tài khoản hoặc mật khẩu";

            }

        }

    }

}
</script>