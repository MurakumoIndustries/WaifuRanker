<template>
    <nav class="navbar fixed-top navbar-expand-lg navbar-light bg-light">
        <a class="pr-2" href="../">
            <i class="icon icon-murakumo"></i>
        </a>
        <a class="navbar-brand" title="Murakumo Industries Waifu Ranking Generator" href="#">
            <span class="d-none d-lg-inline-block">Murakumo Industries</span>
            <span class="d-lg-none">MI</span>
            <span>Waifu Ranking</span>
            <span class="d-none d-sm-inline-block">Generator</span>
            <sup>α</sup>
        </a>
        <button
            class="navbar-toggler"
            type="button"
            data-toggle="collapse"
            data-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent"
            aria-expanded="false"
            aria-label="Toggle navigation"
        >
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
                <li class="nav-item"></li>
            </ul>

            <ul class="navbar-nav my-0">
                <li class="nav-item dropdown">
                    <a
                        class="nav-link dropdown-toggle py-0"
                        href="#"
                        role="button"
                        data-toggle="dropdown"
                        aria-haspopup="true"
                        aria-expanded="false"
                    >
                        <i class="icon icon-version"></i>
                        <div class="d-inline-block" style="vertical-align: middle;">
                            <div id="server">{{currentServer.name}}</div>
                            <div
                                class="m-0"
                                style="font-size: 0.75rem;line-height:0.75rem;"
                                id="version"
                            >{{currentServer.version}}</div>
                        </div>
                    </a>
                    <ul class="dropdown-menu dropdown-menu-right">
                        <h6 class="dropdown-header">{{lang["server"]}}</h6>
                        <a
                            v-for="o in allServers"
                            :key="o.id"
                            :class="['dropdown-item',o.id == currentServer.id ? 'active' : '']"
                            :href="'#!/server/' + o.id"
                        >
                            {{o.name}}
                            <p
                                class="m-0"
                                style="font-size:0.75rem;line-height:0.75rem;"
                            >{{o.version}}</p>
                        </a>
                        <div class="dropdown-divider" id="serverDivider"></div>
                        <h6 class="dropdown-header">{{lang["externallink"]}}</h6>
                        <a
                            class="dropdown-item"
                            href="https://colopl.co.jp/alicegearaegis/"
                            target="_blank"
                        >{{lang["officalsite"]}}</a>
                        <a
                            class="dropdown-item"
                            href="https://alice.colopl.jp/news/show"
                            target="_blank"
                        >{{lang["officalannouncement"]}}</a>
                    </ul>
                </li>
                <li class="nav-item dropdown">
                    <a
                        class="nav-link dropdown-toggle"
                        href="#"
                        role="button"
                        data-toggle="dropdown"
                        aria-haspopup="true"
                        aria-expanded="false"
                    >
                        <i class="material-icons">language</i>
                        <span id="currentLang">{{currentLang}}</span>
                    </a>
                    <ul class="dropdown-menu dropdown-menu-right">
                        <a class="dropdown-item" href="#!/lang/ja-JP">日本語</a>
                        <a class="dropdown-item" href="#!/lang/zh-TW">正體中文</a>
                        <a class="dropdown-item" href="#!/lang/en-US">English</a>
                        <a class="dropdown-item" href="#!/lang/zh-CN">简体中文</a>
                    </ul>
                </li>
            </ul>
        </div>
    </nav>
</template>

<script>
import { Data } from "../js/data.js";
import Ui from "../js/ui.js";

export default {
    data: function() {
        return {};
    },
    methods: {},
    computed: {
        currentServer: function() {
            return Data.getCurrentServer();
        },
        allServers: function() {
            return Data.getAllServers();
        },
        currentLang: function() {
            return Ui.getLangText();
        },
        lang: function() {
            return Ui.getAll();
        }
    }
};
</script>
<style scoped>
.icon {
    background-repeat: no-repeat;
    background-size: contain;
    background-position: center;
    display: inline-block;
    vertical-align: middle;
}

.icon.icon-version {
    width: 2.5rem;
    height: 2.5rem;
    opacity: 0.5;
    background-image: url(../img/version.png);
}

.icon.icon-murakumo {
    width: 2.5rem;
    height: 2.5rem;
    background-image: url(../img/murakumo.png);
}
</style>

