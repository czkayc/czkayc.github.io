<template>
  <div id="app">
    <div class="container">
      <div class="theme-toggle" @click="toggleTheme">
        <i :class="isDark ? 'fas fa-sun' : 'fas fa-moon'"></i>
      </div>

      <div class="login-container">
        <div class="login-left">
          <div class="logo">
            <i class="fas fa-lock"></i>
            <h1>欢迎登录</h1>
          </div>

          <form @submit.prevent="handleLogin">
            <div class="input-group">
              <label for="username">用户名</label>
              <input
                type="text"
                id="username"
                v-model="username"
                placeholder="请输入用户名或邮箱"
                :class="{'error': usernameError}"
              >
              <div class="error-message">{{ usernameError }}</div>
            </div>

            <div class="input-group">
              <label for="password">密码</label>
              <input
                :type="showPassword ? 'text' : 'password'"
                id="password"
                v-model="password"
                placeholder="请输入密码"
                :class="{'error': passwordError}"
              >
              <span class="password-toggle" @click="showPassword = !showPassword">
                <i :class="showPassword ? 'fas fa-eye-slash' : 'fas fa-eye'"></i>
              </span>
              <div class="error-message">{{ passwordError }}</div>
            </div>

            <div class="remember-forgot">
              <div class="remember">
                <input type="checkbox" id="remember" v-model="rememberMe">
                <label for="remember">记住我</label>
              </div>
              <a href="#" class="forgot-password">忘记密码?</a>
            </div>

            <button type="submit" class="login-button">登录</button>
          </form>

          <div class="signup-link">
            还没有账号? <a href="#">立即注册</a>
          </div>

          <div class="social-login">
            <div class="social-button">
              <i class="fab fa-weixin"></i>
            </div>
            <div class="social-button">
              <i class="fab fa-qq"></i>
            </div>
            <div class="social-button">
              <i class="fab fa-weibo"></i>
            </div>
            <div class="social-button">
              <i class="fab fa-github"></i>
            </div>
          </div>
        </div>

        <div class="login-right">
          <div class="welcome-text">
            <h2>欢迎回来!</h2>
            <p>登录以访问您的账户并探索更多功能</p>
          </div>

          <div class="features">
            <div class="feature">
              <i class="fas fa-shield-alt"></i>
              <span>高级安全保护</span>
            </div>
            <div class="feature">
              <i class="fas fa-bolt"></i>
              <span>快速响应体验</span>
            </div>
            <div class="feature">
              <i class="fas fa-sync-alt"></i>
              <span>多设备同步</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

:root {
  --primary-color: #6e8efb;
  --secondary-color: #a777e3;
  --text-color: #333;
  --bg-color: #f8f9fa;
  --card-bg: rgba(255, 255, 255, 0.95);
  --input-bg: #fff;
  --shadow-color: rgba(0, 0, 0, 0.1);
  --error-color: #ff4757;
  --success-color: #2ed573;
}

.dark-theme {
  --text-color: #f1f2f6;
  --bg-color: #1e272e;
  --card-bg: rgba(39, 49, 56, 0.95);
  --input-bg: #2d3a44;
  --shadow-color: rgba(0, 0, 0, 0.3);
}

body {
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  color: var(--text-color);
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  transition: background 0.5s ease;
}

.container {
  width: 100%;
  max-width: 1200px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.theme-toggle {
  position: absolute;
  top: 20px;
  right: 20px;
  background: var(--card-bg);
  width: 50px;
  height: 50px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  box-shadow: 0 5px 15px var(--shadow-color);
  z-index: 10;
}

.login-container {
  display: flex;
  width: 100%;
  max-width: 900px;
  min-height: 500px;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 15px 40px var(--shadow-color);
}

.login-left {
  flex: 1;
  background: var(--card-bg);
  padding: 40px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.login-right {
  flex: 1;
  background: linear-gradient(135deg, rgba(110, 142, 251, 0.7), rgba(167, 119, 227, 0.7));
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 40px;
  color: white;
  text-align: center;
}

.logo {
  text-align: center;
  margin-bottom: 30px;
}

.logo i {
  font-size: 50px;
  color: var(--primary-color);
  margin-bottom: 10px;
}

.logo h1 {
  font-size: 28px;
  font-weight: 600;
}

.input-group {
  margin-bottom: 20px;
  position: relative;
}

.input-group label {
  display: block;
  margin-bottom: 8px;
  font-weight: 500;
}

.input-group input {
  width: 100%;
  padding: 15px;
  background: var(--input-bg);
  border: 1px solid #ddd;
  border-radius: 10px;
  font-size: 16px;
  transition: border 0.3s;
  color: var(--text-color);
}

.input-group input:focus {
  border-color: var(--primary-color);
  outline: none;
}

.password-toggle {
  position: absolute;
  right: 15px;
  top: 45px;
  color: #999;
  cursor: pointer;
}

.error-message {
  color: var(--error-color);
  font-size: 14px;
  margin-top: 5px;
  min-height: 20px;
}

.remember-forgot {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 25px;
}

.remember {
  display: flex;
  align-items: center;
}

.remember input {
  margin-right: 8px;
}

.forgot-password {
  color: var(--primary-color);
  text-decoration: none;
  font-size: 14px;
}

.login-button {
  width: 100%;
  padding: 15px;
  background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
  border: none;
  border-radius: 10px;
  color: white;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: transform 0.2s, opacity 0.2s;
}

.login-button:hover {
  opacity: 0.9;
}

.login-button:active {
  transform: scale(0.98);
}

.signup-link {
  text-align: center;
  margin-top: 25px;
}

.signup-link a {
  color: var(--primary-color);
  text-decoration: none;
  font-weight: 500;
}

.welcome-text h2 {
  font-size: 32px;
  margin-bottom: 20px;
}

.welcome-text p {
  font-size: 18px;
  line-height: 1.6;
  margin-bottom: 30px;
}

.features {
  text-align: left;
  width: 100%;
  max-width: 300px;
}

.feature {
  display: flex;
  align-items: center;
  margin-bottom: 20px;
}

.feature i {
  font-size: 24px;
  margin-right: 15px;
  background: rgba(255, 255, 255, 0.2);
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.social-login {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-top: 30px;
}

.social-button {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: var(--card-bg);
  border: 1px solid #eee;
  cursor: pointer;
  transition: all 0.3s;
  color: var(--text-color);
}

.social-button:hover {
  transform: translateY(-3px);
  box-shadow: 0 5px 15px var(--shadow-color);
}

/* 响应式设计 */
@media (max-width: 768px) {
  .login-container {
    flex-direction: column;
    max-width: 450px;
  }

  .login-right {
    display: none;
  }

  .logo h1 {
    font-size: 24px;
  }
}

@media (max-width: 480px) {
  .login-left {
    padding: 30px 20px;
  }

  .remember-forgot {
    flex-direction: column;
    align-items: flex-start;
    gap: 10px;
  }

  .forgot-password {
    margin-left: 28px;
  }
}
</style>
