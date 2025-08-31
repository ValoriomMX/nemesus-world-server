<template>
<div class="loginshow" style="overflow: hidden" v-if="loginshow">
    <div class="gaming-login-container">
        <div class="gaming-login-bg"></div>
        <div class="gaming-login-content">
            <div class="gaming-login-form gaming-card gaming-fade-in">
                <div class="gaming-login-logo">
                    <img src="../assets/images/logo.png" alt="Logo" class="gaming-logo">
                    <h1 class="gaming-title gaming-glow">Nemesus World</h1>
                </div>
                
                <div class="gaming-login-fields">
                    <div class="gaming-alert danger" v-if="warning">
                        <i class="fas fa-exclamation-triangle"></i>
                        <strong>{{warning}}</strong>
                    </div>
                    
                    <div class="gaming-input-group">
                        <div class="gaming-input-wrapper">
                            <input 
                                class="gaming-input" 
                                type="text" 
                                id="name" 
                                name="name" 
                                v-model="username" 
                                placeholder="Benutzername" 
                                maxlength="35" 
                                autocomplete="off" 
                                v-on:keyup.enter="onEnter" 
                                autofocus
                            >
                            <i class="fas fa-user gaming-input-icon"></i>
                        </div>
                    </div>
                    
                    <div class="gaming-input-group">
                        <div class="gaming-input-wrapper">
                            <input 
                                class="gaming-input" 
                                type="password" 
                                name="password" 
                                id="password" 
                                v-model="password" 
                                placeholder="Passwort" 
                                maxlength="35" 
                                autocomplete="off" 
                                v-on:keyup.enter="onEnter"
                            >
                            <i class="fas fa-lock gaming-input-icon"></i>
                        </div>
                    </div>
                    
                    <div class="gaming-login-actions">
                        <button 
                            type="submit" 
                            class="gaming-btn gaming-btn-login" 
                            @click="login()"
                            :disabled="clicked"
                        >
                            <i class="fas fa-sign-in-alt"></i>
                            <span>{{clicked ? 'Anmelden...' : 'Anmelden'}}</span>
                        </button>
                        
                        <div class="gaming-login-register">
                            <a href="#" class="gaming-text gaming-accent-text" @click="showRegister()">
                                <i class="fas fa-user-plus"></i>
                                Konto erstellen
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: 'LoginWindow',
    data: function () {
        return {
            loginshow: false,
            username: '',
            password: '',
            warning: '',
            clicked: false
        }
    },
    methods: {
        onEnter: function () {
            this.login();
        },
        login: function () {
            if (this.password.length < 6 || this.username.length < 3) {
                this.warning = 'Name oder Passwort zu kurz!';
                return;
            }
            if (this.password.length > 35 || this.username.length > 35) {
                this.warning = 'Name oder Passwort zu kurz!';
                return;
            }
            // eslint-disable-next-line no-undef
            mp.trigger('Client:AccountLogin', this.username, this.password);
            this.clicked = true;
        },
        showLogin: function () {
            this.loginshow = !this.loginshow;
            return;
        },
        showRegister: function () {
            this.loginshow = !this.loginshow;
            mp.trigger('Client:ShowRegister');
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
@import '../assets/css/gaming-theme.css';

/* Gaming Login Specific Styles */
.gaming-login-container {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 9999;
}

.gaming-login-bg {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, 
        var(--bg-primary) 0%, 
        var(--bg-secondary) 50%, 
        var(--bg-primary) 100%);
    background-image: 
        radial-gradient(circle at 20% 50%, rgba(0, 212, 255, 0.1) 0%, transparent 50%),
        radial-gradient(circle at 80% 20%, rgba(0, 212, 255, 0.05) 0%, transparent 50%),
        radial-gradient(circle at 40% 80%, rgba(0, 212, 255, 0.08) 0%, transparent 50%);
    animation: backgroundFloat 20s ease-in-out infinite;
}

@keyframes backgroundFloat {
    0%, 100% { 
        background-position: 0% 50%; 
    }
    50% { 
        background-position: 100% 50%; 
    }
}

.gaming-login-content {
    position: relative;
    z-index: 10;
    width: 100%;
    max-width: 450px;
    padding: 20px;
}

.gaming-login-form {
    padding: 40px;
    text-align: center;
    border: 1px solid rgba(0, 212, 255, 0.2);
}

.gaming-login-logo {
    margin-bottom: 40px;
}

.gaming-logo {
    width: 80px;
    height: 80px;
    margin-bottom: 20px;
    filter: drop-shadow(0 0 10px rgba(0, 212, 255, 0.3));
}

.gaming-login-form h1 {
    font-size: 2.5rem;
    margin-bottom: 10px;
    background: var(--gradient-accent);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

.gaming-login-fields {
    margin-bottom: 20px;
}

.gaming-input-group {
    margin-bottom: 24px;
}

.gaming-input-wrapper {
    position: relative;
}

.gaming-input {
    width: 100%;
    padding: 16px 20px 16px 50px;
    font-size: 16px;
    border: 1px solid var(--border-primary);
    background: rgba(42, 43, 46, 0.8);
    color: var(--text-primary);
    border-radius: 12px;
    transition: all 0.3s ease;
}

.gaming-input:focus {
    border-color: var(--accent-primary);
    background: rgba(42, 43, 46, 0.95);
    box-shadow: 0 0 0 3px rgba(0, 212, 255, 0.1);
    outline: none;
}

.gaming-input-icon {
    position: absolute;
    left: 18px;
    top: 50%;
    transform: translateY(-50%);
    color: var(--text-muted);
    font-size: 16px;
    transition: color 0.3s ease;
}

.gaming-input:focus + .gaming-input-icon {
    color: var(--accent-primary);
}

.gaming-login-actions {
    text-align: center;
}

.gaming-btn-login {
    width: 100%;
    padding: 16px 32px;
    font-size: 16px;
    font-weight: 600;
    margin-bottom: 24px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
}

.gaming-btn-login:disabled {
    opacity: 0.7;
    cursor: not-allowed;
    transform: none;
}

.gaming-btn-login:disabled:hover {
    transform: none;
    box-shadow: 0 4px 15px rgba(0, 212, 255, 0.3);
}

.gaming-login-register {
    padding: 16px 0;
}

.gaming-login-register a {
    color: var(--text-secondary);
    text-decoration: none;
    font-size: 14px;
    transition: all 0.3s ease;
    display: inline-flex;
    align-items: center;
    gap: 8px;
}

.gaming-login-register a:hover {
    color: var(--accent-primary);
    text-decoration: none;
    text-shadow: 0 0 8px rgba(0, 212, 255, 0.4);
}

.gaming-alert {
    margin-bottom: 24px;
    padding: 16px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    gap: 12px;
    font-size: 14px;
}

.gaming-alert.danger {
    background: rgba(255, 68, 68, 0.1);
    border: 1px solid rgba(255, 68, 68, 0.3);
    color: #ff6b6b;
}

/* Responsive Design */
@media (max-width: 576px) {
    .gaming-login-content {
        padding: 15px;
        max-width: 100%;
    }
    
    .gaming-login-form {
        padding: 30px 20px;
    }
    
    .gaming-login-form h1 {
        font-size: 2rem;
    }
}
</style>
