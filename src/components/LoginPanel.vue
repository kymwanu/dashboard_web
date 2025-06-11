<template>
  <div class="login-outer">
    <div class="login-container">
      <div class="login-panel">
        <h2><span class="welcome">Seja</span> <b>bem vindo</b></h2>
        <p class="subtitle">
          Entre na tua conta, viaje pelo nosso mundo e comece a se beneficiar dos nossos serviços
        </p>
        <form @submit.prevent="handleLogin">
          <div class="form-group">
            <label for="username">Email</label>
            <input
              type="email"
              id="username"
              v-model="username"
              placeholder="admin"
              required
              autocomplete="username"
            />
          </div>
          <div class="form-group">
            <label for="password">Password</label>
            <input
              type="password"
              id="password"
              v-model="password"
              placeholder="********"
              required
              autocomplete="current-password"
            />
          </div>
          <button type="submit" class="sign-in-btn">Entrar</button>
          <p v-if="errorMessage" class="error">{{ errorMessage }}</p>
        </form>
        <a href="#" class="forgot">Esqueceu a palavra-passe ?</a>
      </div>
      <div class="side-panel">
        <div class="side-content">
          <h3>
            Construa <span class="highlight">plataformas</span><br />
            que entreguem<b> resultados positivos</b>
          </h3>
          <div class="side-actions">
            <button class="register-btn">Cadastre-se</button>
            <button class="try-btn">Experimente grátis</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const username = ref('')
const password = ref('')
const errorMessage = ref('')
const router = useRouter()

const handleLogin = () => {
  if (username.value === 'admin@gmail.com' && password.value === 'password') {
    router.push('/dashboard')
  } else {
    errorMessage.value = 'Invalid username or password'
  }
}
</script>

<style scoped>
/* Wrapper para centralizar tudo na tela */
.login-outer {
  min-height: 100vh;
  width: 100vw;
  background: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Container do formulário e painel lateral */
.login-container {
  display: flex;
  max-width: 820px;
  width: 100%;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 24px;
  overflow: hidden;
  box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.12);
  transition: all 0.3s;
  margin: 0 16px;
}

.login-panel {
  flex: 1.1;
  background: rgba(30, 41, 59, 0.92);
  color: #fff;
  padding: 48px 36px 36px 36px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  min-width: 0;
  max-width: 380px;
  width: 100%;
  border-top-left-radius: 24px;
  border-bottom-left-radius: 24px;
}

.welcome {
  font-weight: 400;
}

.subtitle {
  color: #b0b8c1;
  font-size: 1rem;
  margin-bottom: 32px;
}

.form-group {
  margin-bottom: 18px;
  display: flex;
  flex-direction: column;
}

label {
  font-size: 0.98rem;
  margin-bottom: 6px;
  color: #b0b8c1;
  text-align: left; /* Alinha o texto à esquerda */
  width: 100%;
}

input[type='email'],
input[type='password'] {
  padding: 12px 14px;
  border-radius: 8px;
  border: 1px solid #334155;
  background: rgba(255, 255, 255, 0.08);
  color: #fff;
  font-size: 1rem;
  outline: none;
  transition: border 0.2s;
}

input[type='email']:focus,
input[type='password']:focus {
  border: 1.5px solid #38e6b0;
}

.sign-in-btn {
  width: 100%;
  padding: 12px 0;
  background: #38e6b0;
  color: #222;
  border: none;
  border-radius: 8px;
  font-size: 1.08rem;
  font-weight: 600;
  margin-top: 8px;
  cursor: pointer;
  transition: background 0.2s;
}

.sign-in-btn:hover {
  background: #2fd39e;
}

.error {
  color: #ff6b6b;
  margin-top: 10px;
  font-size: 0.98rem;
}

.forgot {
  display: block;
  margin-top: 18px;
  color: #b0b8c1;
  font-size: 0.98rem;
  text-align: center;
  text-decoration: none;
  transition: color 0.2s;
}

.forgot:hover {
  color: #38e6b0;
}

.side-panel {
  flex: 1.2;
  background: #fff;
  color: #222;
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  min-width: 0;
  max-width: 380px;
  width: 100%;
  border-top-right-radius: 24px;
  border-bottom-right-radius: 24px;
}

.side-content {
  z-index: 2;
  padding: 48px 36px 36px 36px;
  position: relative;
}

.side-panel h3 {
  font-size: 1.5rem;
  font-weight: 400;
  margin-bottom: 28px;
  margin-top: 0;
}

.highlight {
  background: #222;
  color: #38e6b0;
  padding: 2px 8px;
  border-radius: 6px;
  font-weight: 700;
}

.side-actions {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
}

.register-btn,
.try-btn {
  padding: 10px 22px;
  border-radius: 8px;
  border: 1.5px solid #38e6b0;
  background: transparent;
  color: #38e6b0;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  transition:
    background 0.2s,
    color 0.2s;
}

.register-btn:hover,
.try-btn:hover {
  background: #38e6b0;
  color: #fff;
}

/* Tablets */
@media (max-width: 900px) {
  .login-container {
    flex-direction: column;
    max-width: 98vw;
    margin: 0 8px;
    border-radius: 18px;
  }
  .login-panel,
  .side-panel {
    border-radius: 0;
    border-bottom-left-radius: 18px;
    border-bottom-right-radius: 18px;
    padding: 32px 8vw 24px 8vw;
    max-width: 100%;
  }
  .side-panel {
    min-height: 220px;
  }
  .side-content {
    padding: 32px 8vw 24px 8vw;
  }
}

/* Celulares */
@media (max-width: 600px) {
  .login-container {
    flex-direction: column;
    max-width: 100vw;
    margin: 0;
    border-radius: 0;
    box-shadow: none;
    min-height: 100vh;
  }
  .login-panel,
  .side-panel {
    border-radius: 0;
    padding: 24px 4vw 18px 4vw;
    min-width: 0;
    max-width: 100vw;
  }
  .side-content {
    padding: 24px 4vw 18px 4vw;
  }
  .side-panel h3 {
    font-size: 1rem;
    margin-bottom: 14px;
  }
  .side-actions {
    gap: 8px;
  }
  .register-btn,
  .try-btn {
    font-size: 0.95rem;
    padding: 8px 10px;
  }
  .form-group label,
  .forgot,
  .error {
    font-size: 0.93rem;
  }
  .sign-in-btn {
    font-size: 0.98rem;
    padding: 10px 0;
  }
}

/* Esconde o painel lateral em telas muito pequenas */
@media (max-width: 430px) {
  .side-panel {
    display: none;
  }
  .login-panel {
    border-radius: 0;
    padding: 32px 6vw 24px 6vw;
    max-width: 100vw;
  }
}
</style>
