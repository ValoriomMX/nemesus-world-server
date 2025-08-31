<template>
<div id="app">
    <Loading ref="loading" />
    <Login ref="login" />
    <Register ref="register" />
    <CharacterSwitch ref="characterswitch" />
    <CharacterCreator ref="charactercreator" />
    <Bank ref="bank" />
    <Hud ref="hud" />
    <Menu ref="menu" />
    <RPQuiz ref="rpquiz" />
    <Inventory ref="inventory" />
    <SelectWheel ref="selectwheel" />
    <Speedometer ref="speedometer" />
    <Furniture ref="furniture" />
    <Spediteur ref="spediteur" />
    <Shop ref="shop" />
    <Smartphone ref="smartphone" />
    <Progressbar ref="progressbar" />
    <MDC ref="mdc" />
</div>
</template>

<script>
import Loading from './components/Loading.vue'
import Login from './components/Login.vue'
import Register from './components/Register.vue'
import CharacterSwitch from './components/CharacterSwitch.vue'
import CharacterCreator from './components/CharacterCreator.vue'
import Hud from './components/Hud.vue'
import Menu from './components/Menu.vue'
import RPQuiz from './components/RPQuiz.vue'
import Inventory from './components/Inventory.vue'
import SelectWheel from './components/SelectWheel.vue'
import Speedometer from './components/Speedometer.vue'
import Furniture from './components/Furniture.vue'
import Bank from './components/Bank.vue'
import Spediteur from './components/Spediteur.vue'
import Shop from './components/Shop.vue'
import Smartphone from './components/Smartphone.vue'
import Progressbar from './components/Progressbar.vue'
import MDC from './components/MDC.vue'

export default {
    name: 'App',
    components: {
        Loading,
        Login,
        Register,
        CharacterSwitch,
        CharacterCreator,
        Hud,
        Menu,
        RPQuiz,
        Inventory,
        SelectWheel,
        Speedometer,
        Furniture,
        Bank,
        Spediteur,
        Shop,
        Smartphone,
        Progressbar,
        MDC
    },
    mounted() {
        global.gui.loading = this.$refs.loading;
        global.gui.login = this.$refs.login;
        global.gui.register = this.$refs.register;
        global.gui.characterswitch = this.$refs.characterswitch;
        global.gui.charactercreator = this.$refs.charactercreator;
        global.gui.hud = this.$refs.hud;
        global.gui.menu = this.$refs.menu;
        global.gui.rpquiz = this.$refs.rpquiz;
        global.gui.inventory = this.$refs.inventory;
        global.gui.selectwheel = this.$refs.selectwheel;
        global.gui.speedometer = this.$refs.speedometer;
        global.gui.furniture = this.$refs.furniture;
        global.gui.bank = this.$refs.bank;
        global.gui.spediteur = this.$refs.spediteur;
        global.gui.shop = this.$refs.shop;
        global.gui.smartphone = this.$refs.smartphone;
        global.gui.progressbar = this.$refs.progressbar;
        global.gui.mdc = this.$refs.mdc;
    },
}
</script>

<style>
@import './assets/adminlte/dist/css/adminlte.css';
@import './assets/adminlte/plugins/fontawesome-free/css/all.css';
@import './assets/css/main.css';

#app {
    background: var(--primary-bg);
    min-height: 100vh;
    font-family: 'Rajdhani', sans-serif;
}

html,
body,
* {
    -webkit-user-select: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -o-user-select: none;
    user-select: none;
}

/* Gaming Scrollbars */
::-webkit-scrollbar-thumb {
    background: var(--gradient-accent);
    border-radius: var(--radius-md);
}

::-webkit-scrollbar-thumb:hover {
    background: var(--accent-blue);
}

::-webkit-scrollbar-track {
    background: var(--secondary-bg);
    border-radius: var(--radius-md);
}

::-webkit-scrollbar-corner {
    background: transparent;
}

::-webkit-scrollbar {
    width: 8px;
    height: 8px;
}

body {
    background: var(--primary-bg);
    margin: 0;
    height: 100vh;
    overflow: hidden;
    color: var(--text-primary);
}

/* Gaming Effects */
@keyframes firework {
    0% {
        transform: translate(var(--x), var(--initialY));
        width: var(--initialSize);
        opacity: 1;
    }

    50% {
        width: 0.5vmin;
        opacity: 1;
    }

    100% {
        width: var(--finalSize);
        opacity: 0;
    }
}

@keyframes glow-pulse {
    0%, 100% {
        box-shadow: 0 0 5px var(--accent-blue);
    }
    50% {
        box-shadow: 0 0 20px var(--accent-blue), 0 0 30px var(--accent-blue);
    }
}

/* Gaming Card Animations */
@keyframes card-hover {
    0% {
        transform: translateY(0) scale(1);
    }
    100% {
        transform: translateY(-10px) scale(1.02);
    }
}

/* Override AdminLTE dark mode with gaming theme */
.dark-mode {
    background: var(--primary-bg) !important;
    color: var(--text-primary) !important;
}

.dark-mode .card {
    background: var(--card-bg) !important;
    border-color: var(--border-color) !important;
}

.dark-mode .btn-primary {
    background: var(--gradient-primary) !important;
    border: none !important;
}

.dark-mode .btn-primary:hover {
    background: var(--gradient-accent) !important;
    transform: translateY(-2px);
    box-shadow: var(--shadow-glow);
}
</style>
