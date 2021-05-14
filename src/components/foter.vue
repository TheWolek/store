<template>
  <footer>
    <section id="help">
      <h3>Pomoc</h3>
      <a>Pomoc i kontakt</a>
      <a>FAQ</a>
      <a>Tabele rozmiarowe</a>
      <a>Zwroty i reklamacja</a>
    </section>
    <section id="orders">
      <h3>Zamówienia</h3>
      <a>Dostawa</a>
      <a>Zwroty i reklamacja</a>
    </section>
    <section id="contact">
      <h3>Kontakt</h3>
      <div class="contact-phone">
        <img src="../assets/phone.png" />
        <p>34 500 00 00</p>
      </div>
      <div class="contact-mail">
        <img src="../assets/mail.png" />
        <p>kontakt@store.com</p>
      </div>
    </section>
    <div class="copyright">
      <p>© store 2021</p>
      <div>
        Icons made by
        <a href="https://www.freepik.com" title="Freepik">Freepik</a> and
        <a href="https://www.flaticon.com/authors/iconixar" title="iconixar"
          >iconixar</a
        >
        from
        <a href="https://www.flaticon.com/" title="Flaticon"
          >www.flaticon.com</a
        >
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Foter",
};
</script>

<style lang="scss">
@import "../styles/common.scss";

footer {
  display: flex;
  flex-wrap: wrap;
  border-top: 3px solid #000;
  padding: 1.5em 0 0 1em;
  gap: 2em;
  margin-top: 4em;

  section {
    width: 100%;
  }

  #contact {
    order: -1;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 0.8em;
    h3 {
      //   font-size: 1.3rem;
      font-size: clamp(1.3rem, 4vw, 1rem);
      font-weight: bold;
      margin-bottom: 0.3em;
    }

    img {
      height: 20px;
    }

    div {
      display: flex;
      gap: 0.5em;
      //   font-size: 0.9rem;
      font-size: clamp(0.9rem, 4vw, 1rem);
      align-items: center;

      p {
        margin: 0;
      }
    }

    .contact-phone {
      p {
        // font-size: 1.3rem;
        font-size: clamp(1.3rem, 4vw, 1.2rem);
      }
    }
  }

  #help,
  #orders {
    display: flex;
    flex-direction: column;
    align-items: flex-start;

    h3 {
      //   font-size: 1.3rem;
      font-size: clamp(1.3rem, 4vw, 1rem);
      font-weight: bold;
    }

    a {
      font-size: 1rem;
      font-size: clamp(1rem, 4vw, 1rem);

      &:hover {
        cursor: pointer;
        color: darken($font-dark, 10%);
        font-weight: bold;
      }
    }
  }

  .copyright {
    order: 4;
    margin: 0;
    width: 100%;
    font-size: 0.9rem;
  }
}

@media screen and (min-width: 1024px) {
  footer {
    flex-direction: row;
    justify-content: center;
    padding: 2em 0;

    section {
      width: 30%;
    }

    #contact {
      order: 3;
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      gap: 0.5em;
      h3 {
        //   font-size: 1.3rem;
        font-size: clamp(1.3rem, 4vw, 1rem);
        font-weight: bold;
        margin-bottom: 0;
      }

      img {
        height: 20px;
      }

      div {
        display: flex;
        gap: 0.5em;
        //   font-size: 0.9rem;
        font-size: clamp(0.9rem, 4vw, 1rem);
        align-items: center;

        p {
          margin: 0;
        }
      }

      .contact-phone {
        p {
          // font-size: 1.3rem;
          font-size: clamp(1.3rem, 4vw, 1.2rem);
        }
      }
    }
  }
}
</style>
