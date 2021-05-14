<template>
  <div class="wrap">
    <div class="login-box">
      <form>
        <h3>Zaloguj się</h3>
        <div class="form-group">
          <label for="login">Login:</label>
          <input type="text" id="L-login" name="login" class="form-control" />
        </div>
        <div class="form-group">
          <label for="pass">Hasło:</label>
          <input type="password" id="L-pass" name="pass" class="form-control" />
        </div>
        <input type="submit" value="Zaloguj się" class="btn-primary" />
      </form>
    </div>
    <div class="register-box">
      <form>
        <h3>Nie masz konta? Zarejestruj się</h3>
        <div class="from-group">
          <label for="R-name">Imię:</label>
          <input type="text" id="R-name" name="name" class="form-control" />
        </div>
        <div class="from-group">
          <label for="R-surname">Nazwisko:</label>
          <input
            type="text"
            id="R-surname"
            name="surname"
            class="form-control"
          />
        </div>
        <div class="from-group">
          <label for="R-mail">E-mail:</label>
          <input type="email" id="R-mail" name="mail" class="form-control" />
        </div>
        <div class="from-group">
          <label for="R-pass">Hasło:</label>
          <input type="password" id="R-pass" name="pass" class="form-control" />
        </div>
        <div class="form-check">
          <input
            type="checkbox"
            id="R-reg"
            name="R-reg"
            value=""
            class="form-check-input"
          />
          <label for="R-reg" class="form-check-label"
            >Akceptuje Regulamin</label
          >
        </div>
        <input type="submit" value="Załóż konto" class="btn-primary" />
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "Login",
};
</script>

<style lang="scss">
@import "../../styles/common.scss";

.wrap {
  width: 100%;
  display: flex;
  justify-content: space-around;
  align-items: flex-start;
  gap: 2em;
  padding: 2em 0;

  input[type="submit"] {
    padding: 0.5em 1.2em;
    border: none;
    outline: none;
    border-radius: 4%;
  }

  .login-box,
  .register-box {
    padding: 3em 6em;
  }

  .login-box {
    // box-shadow: 1px 5px 15px 3px rgba(0, 0, 0, 0.29);
    // padding: 3em 6em;
    border-radius: 3%;
  }
}
</style>
