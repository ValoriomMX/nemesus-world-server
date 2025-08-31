<template>
<div class="registershow" style="overflow: hidden" v-if="registershow">
    <div class="limiter">
        <div class="container-login100">
            <div class="wrap-login100 gaming-card" style="margin-top: 15vh; max-width: 450px; padding: 40px;">
                <div class="login100-form-avatar" style="margin-bottom: 30px;">
                    <img src="../assets/images/logo.png" alt="Logo" style="width: 80px; height: 80px; border-radius: 50%; border: 3px solid var(--accent-blue); box-shadow: var(--shadow-glow);">
                </div>
                <h2 class="text-center mb-4" style="color: var(--text-primary); font-family: 'Orbitron', sans-serif;">Crear Cuenta</h2>
                <div class="wrap-input100 m-b-10 mt-1">
                    <div class="alert alert-danger text-center gaming-card" role="alert" style="border-radius: 25px; background: var(--danger); border: none;" v-if="warning">
                        <strong>Info: {{warning}}</strong>
                    </div>
                    <div class="wrap-input100 mt-3">
                        <input class="input100" type="text" id="name" name="name" v-model="username" placeholder="Nombre de usuario" maxlength="35" autocomplete="off" v-on:keyup.enter="onEnter" autofocus style="padding: 15px 50px 15px 15px; font-size: 16px;">
                        <span class="focus-input100"></span>
                        <span class="symbol-input100" style="position: absolute; right: 15px; top: 50%; transform: translateY(-50%); color: var(--accent-blue);">
                            <i class="fa fa-user"></i>
                        </span>
                    </div>
                </div>
                <div class="wrap-input100 m-b-10">
                    <input class="input100" type="password" name="password" id="password" v-model="password" placeholder="Contraseña" maxlength="35" autocomplete="off" v-on:keyup.enter="onEnter" style="padding: 15px 50px 15px 15px; font-size: 16px;">
                    <span class="focus-input100"></span>
                    <span class="symbol-input100" style="position: absolute; right: 15px; top: 50%; transform: translateY(-50%); color: var(--accent-blue);">
                        <i class="fa fa-lock"></i>
                    </span>
                </div>
                <div class="wrap-input100 m-b-20">
                    <input class="input100" type="password" name="password2" id="password2" v-model="password2" placeholder="Repetir contraseña" maxlength="35" autocomplete="off" v-on:keyup.enter="onEnter" style="padding: 15px 50px 15px 15px; font-size: 16px;">
                    <span class="focus-input100"></span>
                    <span class="symbol-input100" style="position: absolute; right: 15px; top: 50%; transform: translateY(-50%); color: var(--accent-blue);">
                        <i class="fa fa-lock"></i>
                    </span>
                </div>
                <div class="container-login100-form-btn p-t-10" v-if="!clicked">
                    <button type="submit" class="login100-form-btn btn-gaming-success" @click="register()" style="width: 100%; padding: 15px; font-size: 18px; margin-bottom: 20px;">
                        Continuar
                    </button>
                </div>
                <div class="container-login100-form-btn p-t-10" v-else>
                    <button type="submit" disabled class="login100-form-btn" @click="register()" style="width: 100%; padding: 15px; font-size: 18px; margin-bottom: 20px;">
                        Procesando...
                    </button>
                </div>
                <div class="text-center w-full mb-3">
                    <a href="#" class="txt1" @click="showLogin()">
                        ¿Ya tienes cuenta? Inicia sesión aquí
                    </a>
                </div>
                <div class="text-center w-full">
                    <a href="#" class="txt1" style="font-size: 14px; color: var(--text-muted);">
                        Servidor desarrollado por <strong style="color: var(--accent-blue);">Nemesus.de</strong>
                    </a>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: 'RegisterWindow',
    data: function () {
        return {
            registershow: false,
            username: '',
            password: '',
            password2: '',
            warning: '',
            clicked: false
        }
    },
    methods: {
        onEnter: function () {
            this.register();
        },
        register: function () {
            // eslint-disable-next-line no-undef
            if (this.password.length < 6 || this.username.length < 3) {
                this.warning = '¡Usuario o contraseña demasiado corto!';
                return;
            }
            if (this.password.length > 35 || this.username.length > 35) {
                this.warning = '¡Usuario o contraseña demasiado largo!';
                return;
            }
            if (this.password === this.password2) {
                // eslint-disable-next-line no-undef
                mp.trigger('Client:AccountRegister', this.username, this.password);
                this.clicked = true;
                return;
            } else {
                this.warning = '¡Las contraseñas no coinciden!';
                return;
            }
        },
        showRegister: function () {
            this.registershow = !this.registershow;
            return;
        },
        showLogin: function () {
            this.registershow = !this.registershow;
            mp.trigger('Client:ShowLogin');
            return;
        },
        setWarning: function (text) {
            this.warning = text;
            this.clicked = false;
            return;
        }
    }
}
</script>

<style scoped>
@import '../assets/css/bootstrap.min.css';
@import '../assets/css/main.css';
@import '../assets/css/util.css';
@import '../assets/css/font-awesome.min.css';

html,
body,
template,
* {
    -webkit-user-select: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -o-user-select: none;
    user-select: none;
}
</style>
