<template>
  <div class="wrap">
    <div class="box">
      <form>
        <h3>Zarejestruj się</h3>
        <div class="form-group">
          <label for="R-name">Imię:</label>
          <input type="text" id="R-name" name="name" class="form-control" />
        </div>
        <div class="form-group">
          <label for="R-surname">Nazwisko:</label>
          <input
            type="text"
            id="R-surname"
            name="surname"
            class="form-control"
          />
        </div>
        <div class="form-group">
          <label for="R-mail">E-mail:</label>
          <input type="email" id="R-mail" name="email" class="form-control" />
        </div>
        <div class="form-group">
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

      <p>Masz już konto? <router-link to="/login">Zaloguj się</router-link></p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Register",
};
</script>

<style lang="scss" scoped>
.wrap {
  p {
    margin-top: 2em;
    font-size: 0.9rem;

    a {
      display: inline;
      padding: 0;
    }
  }

  .box {
    width: 100%;
    box-shadow: 0px 5px 15px -4px rgba(0, 0, 0, 0.4);
  }

  .form-group {
    margin-bottom: 0.7em;

    label {
      width: 100%;
      text-align: left;
      padding-left: 0.3em;
    }
  }
}

@media screen and (min-width: 768px) {
  .wrap {
    .box {
      width: 80%;
    }
  }
}

@media screen and (min-width: 1024px) {
  .wrap {
    .box {
      width: 30%;

      .form-control {
        margin: 0;
        width: 100%;
      }
    }
  }
}
</style>