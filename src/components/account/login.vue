<template>
  <div class="wrap">
    <div class="box">
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
      <h3>Nie masz konta?</h3>
      <router-link to="/register" class="btn-secondary">
        Załóż konto
      </router-link>
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
  flex-direction: column;
  gap: 3em;
  padding: 2em 0;

  h3 {
    margin-bottom: 1em;
    text-align: left;
    font-weight: bold;
  }

  input[type="submit"],
  a {
    padding: 0.5em 1.2em;
    border: none;
    outline: none;
    border-radius: 7px;
    margin-top: 1em;
    font-size: 14px;
    width: 80%;
  }

  // a {
  //   display: block;
  //   width: 100%;
  //   margin-top: 0;
  // }

  .box {
    box-shadow: 0px 5px 15px -4px rgba(0, 0, 0, 0.4);
    border-radius: 3%;
    // padding: 3em 6em;
    padding: 1em;
    width: 100%;
  }

  .register-box {
    width: 100%;
    padding: 1em;

    a {
      display: block;
      width: 80%;
      margin: 0 auto;
    }
  }
}

@media screen and (min-width: 768px) {
  .wrap {
    align-items: center;
    .box,
    .register-box {
      width: 80%;
    }

    .register-box {
      a {
        width: 80%;
        margin: 0 auto;
      }
    }
  }
}

@media screen and (min-width: 1024px) {
  .wrap {
    flex-direction: row;
    align-items: flex-start;

    .box,
    .register-box {
      width: 30%;
      padding: 2em;
    }

    .box {
      input[type="text"],
      input[type="password"] {
        width: 90%;
        margin: 0 auto;
      }

      input[type="submit"] {
        width: 70%;
      }
    }
  }
}
</style>
