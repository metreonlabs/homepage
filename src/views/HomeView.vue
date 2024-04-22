<template>
  <section id="section" class="hero_container">
    <div class="app_width">
      <div class="hero">
        <div class="hero_text_content">
          <h3 class="title">{{ $t("hero.title") }}</h3>
          <p class="desc">{{ $t("hero.description") }}</p>

          <div class="buttons">
            <a href="https://docs.metreon.xyz/" target="_blank">
              <div class="button">{{ $t("hero.button1") }}</div>
            </a>
            <!-- <a href="" target="_blank">
              <div class="button">{{ $t("hero.button2") }}</div>
            </a> -->
          </div>
        </div>

        <div class="scroll">
          <MouseIcon />
          <p>{{ $t("hero.scroll") }}</p>
        </div>
      </div>
    </div>
  </section>

  <div class="group_container">
    <section id="section" class="what_container">
      <div class="app_width">
        <div class="what">
          <h3 class="what_title">What metreon offers</h3>

          <div class="items">
            <div class="item">
              <TransferIcon />
              <h6>Seamlessly Relay <br> data</h6>
              <p>By making relaying of arbitrary data across multiple blockchains effortless, Dapps on Areon can easily
                maximize their functionalities by going cross-chain.</p>
            </div>

            <div class="item">
              <CoinIcon />
              <h6>Built-in Tokens <br> transfer feature</h6>
              <p>DApps powered by Metreon benefits from the ease of secure transferring of tokenized assets across
                chains
                with the help of the token composability. </p>
            </div>

            <div class="item">
              <NewBlockIcon />
              <h6>One integration for <br> multiple chain support.</h6>
              <p>Integrating your Dapp with Metreon readily unlock it's support for other blockchain i.e BNB chain,
                Polygon and more.</p>
            </div>
          </div>

          <a href="https://docs.metreon.xyz" target="_blank">
            <button class="what_learn">Learn More</button>
          </a>
        </div>
      </div>
    </section>


    <section id="section" class="footer_container">
      <div class="app_width">
        <div class="footer_tabs">
          <div class="footer_tab">
            <h3>Get Started</h3>

            <div class="footer_tab_links">
              <a href="https://docs.metreon.xyz/developers" target="_blank">As a Developer</a>
              <a href="https://docs.metreon.xyz/use-cases/for-users" target="_blank">As a User</a>
            </div>
          </div>

          <div class="footer_tab">
            <h3>Ecosystem</h3>

            <div class="footer_tab_links">
              <a href="https://scan.metreon.xyz" target="_blank">Metreon<span>Scan</span></a>
              <a @click="comingSoon" class="disabled">Beamre</a>
            </div>
          </div>

          <div class="footer_tab">
            <h3>Resources</h3>

            <div class="footer_tab_links">
              <a href="https://docs.metreon.xyz/" target="_blank">Docs</a>
              <a href="https://github.com/metreonlabs" target="_blank">GitHub</a>
            </div>
          </div>

          <div class="footer_tab footer_tab">
            <h3>Community</h3>

            <div class="footer_tab_links footer_social_tab_links">
              <a href="https://t.me/metreonlabs" target="_blank">
                <TelegramIcon />
              </a>
              <a href="https://twitter.com/metreon_labs" target="_blank">
                <XIcon />
              </a>
              <a @click="comingSoon" class="disabled">
                <DiscordIcon />
              </a>
            </div>
          </div>
        </div>
      </div>


      <img src="/images/footer.png" alt="">
    </section>
  </div>
</template>

<script setup>
import CoinIcon from '../components/icons/CoinIcon.vue';
import TransferIcon from '../components/icons/TransferIcon.vue';
import NewBlockIcon from '../components/icons/NewBlockIcon.vue';
import MouseIcon from '../components/icons/MouseIcon.vue';
import TelegramIcon from '../components/icons/TelegramIcon.vue';
import XIcon from '../components/icons/XIcon.vue';
import DiscordIcon from '../components/icons/DiscordIcon.vue';
</script>

<script>
import { notify } from '../reactives/notify';
export default {
  methods: {
    comingSoon: function () {
      notify.push({
        title: "Feature coming soon.",
        description: "Stay updated with us on X to be the first to know!",
        category: "error"
      });
    }
  }
};
</script>

<style scoped>
.hero_container {
  background-image: url('/images/boxes.png');
  background-position: center center;
  background-repeat: no-repeat;
  background-size: 1920px 1080px;
}

.hero {
  display: flex;
  align-items: center;
  flex-direction: column;
  padding-top: 240px;
  padding-bottom: 80px;
}

.hero_text_content {
  width: 730px;
  max-width: 100%;
}

.hero_text_content .title {
  color: var(--tx-normal, #EEF1F8);
  text-align: center;

  font-size: 50px;
  font-style: normal;
  font-weight: 600;
  line-height: 150%;
  /* 75px */
  letter-spacing: 1px;
}



.hero_text_content .desc {
  margin-top: 40px;
  color: var(--tx-semi, #8B909E);
  text-align: center;

  font-size: 16px;
  font-style: normal;
  font-weight: 400;
  line-height: 160%;
  /* 25.6px */
  letter-spacing: 0.32px;
}



.buttons {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 40px;
  margin-top: 110px;
}

.button {
  border-radius: 4px;
  width: 312px;
  max-width: 100%;
  height: 54px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;

  font-size: 16px;
  font-style: normal;
  font-weight: 600;
  line-height: 100%;
  /* 16px */
  letter-spacing: 0.64px;
}

.buttons a:first-child .button {
  color: var(--bg-lightest, #0C1A33);
  background: var(--primary-primary, #00A3FF);
}

/* .buttons a:last-child .button {
  color: var(--tx-normal, #EEF1F8);
  border: 2px solid var(--bg-lightest, #0C1A33);
  background: var(--bg-lighter, #091121);
} */

.scroll {
  display: flex;
  flex-direction: column;
  gap: 20px;
  align-items: center;
  margin-top: 200px;
}

.scroll p {
  color: #EDF0F5;
  text-align: center;
  font-family: Axiforma;
  font-size: 14px;
  font-style: normal;
  font-weight: 500;
  line-height: 100%;
  /* 14px */
  letter-spacing: 0.56px;
}

/*  */

.group_container {
  background-image: url('/images/lines.png');
  background-position: center center;
  background-repeat: no-repeat;
  background-size: 1040px 2000px;
  background-color: #EDF0F5;
  padding-top: 200px;
  max-width: 100%;
}

/*  */

.what_container {}

.what {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.what_title {
  color: #293A59;
  text-align: center;

  font-size: 38px;
  font-style: normal;
  font-weight: 600;
  line-height: 150%;
  /* 57px */
  letter-spacing: 0.76px;
}

.items {
  display: flex;
  flex-wrap: wrap;
  gap: 30px;
  margin-top: 120px;
  margin-bottom: 100px;

  justify-content: center;
}

.item {
  width: 380px;
  max-width: 100%;
  border-radius: 6px;
  background: #FCFDFF;
  padding: 50px 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.item svg {
  background: #F2F5FA;
  width: 40px;
  height: 40px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 6px;
}


.item h6 {
  margin-top: 40px;
  color: #182D40;
  text-align: center;

  font-size: 24px;
  font-style: normal;
  font-weight: 600;
  line-height: 160%;
  /* 38.4px */
  letter-spacing: -0.24px;
  width: 260px;
}

.item p {
  margin-top: 26px;
  color: #ABADAE;
  text-align: center;

  font-size: 16px;
  font-style: normal;
  font-weight: 500;
  line-height: 150%;
  /* 24px */
  letter-spacing: -0.16px;
}

.what_learn {
  border-radius: 4px;
  border: 1px solid #EDF0F5;
  background: #FCFDFF;
  height: 46px;
  width: 195px;

  color: #0C1A33;
  text-align: center;

  font-size: 16px;
  font-style: normal;
  font-weight: 600;
  line-height: 100%;
  /* 16px */
  letter-spacing: 0.64px;

  cursor: pointer;
  user-select: none;
}

/*  */

.footer_container {
  padding-top: 200px;
  padding-bottom: 550px;
  position: relative;
}

.footer_tabs {
  display: flex;
  flex-wrap: wrap;
  gap: 40px;
  max-width: 100%;
  justify-content: space-between;
}

.footer_tab {
  width: 250px;
  max-width: 100%;
}

.footer_tab h3 {
  margin-bottom: 28px;
  font-weight: 600;
  color: #39375C;
  font-size: 20px;
}

.footer_tab_links {
  display: flex;
  flex-direction: column;
}

.footer_tab_links a {
  display: block;
  padding: 10px 0;
  color: #182D40;
  font-size: 16px;
}

.footer_tab_links span {
  font-weight: 600;
}

.footer_container img {
  position: absolute;
  transform: translate(-50%, 0);
  left: 50%;
  bottom: 0;
  width: 1920px;
  max-width: 100%;
}

.footer_social_tab_links {
  flex-direction: row;
  align-items: center;
  gap: 20px;
}

.footer_social_tab_links svg {
  background: #FFFFFF;
  width: 40px;
  height: 40px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 8px;
}

.footer_tab .disabled {
  opacity: 0.5;
}


@media screen and (max-width: 1000px) {
  .hero {
    padding-top: 200px;
    padding-bottom: 60px;
  }


  .scroll {
    margin-top: 120px;
  }

  .hero_text_content .title {
    font-size: 36px;
  }


  .group_container {
    padding-top: 100px;
  }


  .what_title {
    font-size: 24px;
  }

  .items {
    margin-top: 80px;
    margin-bottom: 60px;
  }

  .item {
    padding: 30px 30px;
  }

  .item h6 {
    margin-top: 26px;
    font-size: 20px;
  }

  .item p {
    margin-top: 16px;
    font-size: 14px;
  }

  .footer_tab h3 {
    margin-bottom: 16px;
    font-size: 16px;
  }

  .footer_tab_links a {
    padding: 4px 0;
    font-size: 14px;
  }

  .footer_container {
    padding-top: 100px;
    padding-bottom: 150px;
  }

  .footer_social_tab_links svg {
    width: 36px;
    height: 36px;
  }
}
</style>
