<template>
    <section id="section">
        <div class="app_width">
            <header id="main_header">
                <div class="logo">
                    <MetreonLogo />
                </div>
                <div class="tabs" ref="menu">
                    <a target="_blank" href="https://docs.metreon.xyz/">
                        <div :class="'tab_item'">
                            <p>{{ $t("header.docs") }}</p>
                        </div>
                    </a>
                    <a target="_blank" href="https://github.com/metreonlabs">
                        <div :class="'tab_item'">
                            <p>{{ $t("header.github") }}</p>
                        </div>
                    </a>
                    <a target="_blank" href="https://scan.metreon.xyz">
                        <div :class="'tab_item'">
                            <p>{{ $t("header.scan") }}</p>
                            <OutIcon />
                        </div>
                    </a>
                    <a target="_blank" href="https://bridge.metreon.xyz">
                        <div :class="'tab_item'">
                            <p>{{ $t("header.nftBridge") }}</p>
                            <OutIcon />
                        </div>
                    </a>
                </div>
                <div class="connection">
                    <a href="https://docs.metreon.xyz/" target="_blank">
                        <div class="connection_action">
                            <p>{{ $t("header.startBuilding") }}</p>
                        </div>
                    </a>
                </div>
                <div class="handburger">
                    <div ref="handburger" id="handburger" v-on:click="onDrawer()">
                        <span></span>
                        <span></span>
                        <span></span>
                        <span></span>
                    </div>
                </div>
            </header>
        </div>
    </section>
</template>

<script setup>
// import WalletDownIcon from './icons/WalletDownIcon.vue';
import OutIcon from './icons/OutIcon.vue';
import MetreonLogo from './icons/MetreonLogo.vue';
</script>

<script>
import i18n from "@/i18n";
import { notify } from '../reactives/notify';
export default {
    data() {
        return {
            switching: false,
            aciveCode: i18n.global.locale.value,
            languages: [
                {
                    name: 'English',
                    code: 'en',
                    active: true
                },
                {
                    name: 'Chinese',
                    code: 'ch',
                    active: true
                },
                {
                    name: 'Korean',
                    code: 'kr',
                    active: false
                },
                {
                    name: 'Thai',
                    code: 'th',
                    active: false
                }
            ]
        };
    },
    methods: {
        onDrawer() {
            this.$refs["handburger"].classList.toggle("open");
            this.$refs["menu"].classList.toggle("open-menu");
            document.body.classList.toggle("modal");
        },
        determineGlass() {
            const header = document.getElementById('main_header');
            header.classList.toggle('glass', window.scrollY > 850);
        },
        switchLanguage(lang) {
            if (!lang.active) {
                notify.push({
                    title: "Language support coming soon.",
                    description: "We are working to make Metreon accessible for you!",
                    category: "error"
                });
                return;
            }

            i18n.global.locale.value = lang.code;
            this.aciveCode = lang.code;
        }
    },
    mounted() {
        document.querySelectorAll('.tabs a').forEach(element => {
            element.addEventListener('click', () => {
                context.onDrawer();
            });
        });
        this.determineGlass();
        const context = this;
        window.addEventListener('scroll', function () {
            context.determineGlass();
        });
    }
};
</script>

<style scoped>
section {
    width: 100%;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 5;
}

header {
    width: 100%;
    height: 90px;
    flex-shrink: 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.logo {
    min-width: 190px;
}

.connection {
    display: flex;
    align-items: center;
    gap: 20px;
    justify-content: flex-end;
}

.connection_action {
    border-radius: 4px;
    border: 2px solid var(--background-lightest, #0C1A33);
    background: var(--background-lighter, #091121);
    width: 186px;
    height: 46px;
    display: flex;
    justify-content: center;
    align-items: center;

    color: var(--tx-normal, #EEF1F8);
    text-align: center;

    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    line-height: 100%;
    /* 16px */
    letter-spacing: 0.64px;

    user-select: none;
    cursor: pointer;
}

.logo svg {
    height: 34px;
}

.tabs {
    gap: 60px;
    display: flex;
    align-items: center;
    transition: .2s;
}

.tab_item p {
    color: var(--text-dimmed, #6C6E73);
    font-size: 16px;
    font-style: normal;
    font-weight: 500;
    padding: 4px 0;
    line-height: 16px;
}

.tab_item_active p {
    color: var(--text-normal, #EEF1F8);
}


a .tab_item {
    display: flex;
    align-items: center;
    gap: 12px;
}

a .tab_item svg {
    margin-top: 2px;
}

.current_lang {
    width: 46px;
    height: 46px;
    border-radius: 4px;
    background: var(--bg-lightest, #0C1A33);
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    cursor: pointer;
}

.current_lang svg {
    position: absolute;
    bottom: 2px;
    right: 2px;
}

.langs {
    border-radius: 4px;
    border: 2px solid var(--bg-lighter, #091121);
    background: var(--bg-light, #050C17);
    overflow: hidden;
    width: 184px;
    position: absolute;
    top: 56px;
    right: 0;
    z-index: 1;
}

.lang {
    display: flex;
    align-items: center;
    gap: 8px;
    height: 64px;
    border-bottom: 2px solid var(--bg-lighter, #091121);
    padding: 0 20px;
    cursor: pointer;
}

.lang:hover {
    background: var(--bg-lighter, #050C17);
}

.lang:last-child {
    border: none;
}

.lang p {
    color: var(--tx-normal, #EEF1F8);
    font-size: 16px;
    font-style: normal;
    font-weight: 500;
    line-height: 100%;
    /* 16px */
    letter-spacing: 0.32px;
}

.handburger {
    display: none;
    cursor: pointer;
}

.glass #handburger span {
    background: #0C1A33;
}

@media screen and (max-width: 1000px) {
    .logo {
        min-width: 0px;
    }

    .logo svg {
        height: 26px;
    }

    .tabs {
        position: fixed;
        width: 100%;
        height: 100%;
        z-index: 999;
        top: 0;
        right: -120%;
        flex-direction: column;
        background: var(--bg);
        padding: 60px 20px;
        gap: 0;
    }

    .open-menu {
        right: 0 !important;
    }

    .connection_action {
        width: 150px;
    }

    a {
        display: block;
        width: 100%;
    }

    a .tab_item {
        width: 100%;
        height: 65px;
        border-bottom: 1px solid var(--bg-lightest);
        padding: 0 20px;
    }

    .handburger {
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 2px;
        width: 40px;
        height: 40px;
        z-index: 9999;
    }

    #handburger {
        width: 24px;
        height: 14px;
        position: relative;
        transform: rotate(0deg);
        transition: 0.5s ease-in-out;
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    #handburger span {
        display: block;
        position: absolute;
        height: 2px;
        width: 24px;
        background: #FFFFFF;
        opacity: 1;
        left: 0;
        transform: rotate(0deg);
        transition: 0.25s ease-in-out;
    }

    #handburger span:nth-child(1) {
        top: 0px;
    }

    #handburger span:nth-child(2),
    #handburger span:nth-child(3) {
        top: 6px;
    }

    #handburger span:nth-child(4) {
        top: 12px;
    }


    #handburger.open span:nth-child(1) {
        top: 10px;
        width: 0%;
        left: 50%;
    }

    #handburger.open span:nth-child(2) {
        -webkit-transform: rotate(45deg);
        -moz-transform: rotate(45deg);
        -o-transform: rotate(45deg);
        transform: rotate(45deg);
    }

    #handburger.open span:nth-child(3) {
        -webkit-transform: rotate(-45deg);
        -moz-transform: rotate(-45deg);
        -o-transform: rotate(-45deg);
        transform: rotate(-45deg);
    }

    #handburger.open span:nth-child(4) {
        top: 18px;
        width: 0%;
        left: 50%;
    }
}
</style>