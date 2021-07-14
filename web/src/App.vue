<template>
    <v-app>
        <v-app-bar app color="primary" dark>
            <v-app-bar-nav-icon @click="navigationDrawer = !navigationDrawer"></v-app-bar-nav-icon>
            <v-toolbar-title>MegaGO</v-toolbar-title>
        </v-app-bar>
        <v-navigation-drawer app v-model="navigationDrawer">
            <v-list-item>
                <v-list-item-content>
                    <v-list-item-title class="title">
                        MegaGO
                    </v-list-item-title>
                    <v-list-item-subtitle>
                        Compute similarity
                    </v-list-item-subtitle>
                </v-list-item-content>
            </v-list-item>

            <v-divider></v-divider>

            <v-list dense nav class="py-0 mt-4">
                <div v-for="item of links" :key="item.title">
                    <v-list-item v-if="'link' in item" link :to="item.link">
                        <v-list-item-icon>
                            <v-icon>{{ item.icon }}</v-icon>
                        </v-list-item-icon>
                        <v-list-item-content>
                            <v-list-item-title>{{ item.title }}</v-list-item-title>
                        </v-list-item-content>
                    </v-list-item>
                    <v-list-group v-else :prepend-icon="item.icon">
                        <template v-slot:activator>
                            <v-list-item-title>{{ item.title}}</v-list-item-title>
                        </template>
                        <v-list-item
                            v-for="subitem in item.links"
                            :key="subitem.title"
                            link
                            class="sublist-item"
                            :to="subitem.link">
                            <v-list-item-icon>
                                <v-icon>{{ subitem.icon }}</v-icon>
                            </v-list-item-icon>
                            <v-list-item-content>
                                <v-list-item-title>{{ subitem.title }}</v-list-item-title>
                            </v-list-item-content>
                        </v-list-item>
                    </v-list-group>
                </div>
            </v-list>
        </v-navigation-drawer>
        <v-main class="mx-xs-2 mx-sm-4 mx-md-16">
            <div style="max-width: 1200px;" class="flex-grow-1">
                <router-view></router-view>
            </div>
        </v-main>
        <v-footer dark>
            <div class="text-center" style="width: 100%;">
                <v-btn
                    v-for="icon in icons"
                    :key="icon.link"
                    :href="icon.link"
                    target="_blank"
                    class="mx-4"
                    dark
                    icon>
                    <v-icon size="24px">{{ icon.icon }}</v-icon>
                </v-btn>
                <v-divider class="my-2"></v-divider>
                <div>
                    {{ new Date().getFullYear() }} — <strong>The MegaGO Project</strong>
                </div>
            </div>
        </v-footer>
    </v-app>
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";

@Component
export default class App extends Vue {
    private navigationDrawer = false;

    private links = [
        {
            icon: "mdi-home",
            title: "Home",
            link: "/"
        },
        {
            icon: "mdi-cog-outline",
            title: "Analysis",
            link: "/analysis"
        },
        {
            icon: "mdi-domain",
            title: "About",
            link: "/about"
        },
        {
            icon: "mdi-help-circle-outline",
            title: "Help",
            links: [
                {
                    icon: "mdi-console",
                    title: "CLI",
                    link: "/help/cli"
                },
                {
                    icon: "mdi-web",
                    title: "Web",
                    link: "/help/web"
                }
            ]
        }
    ];

    private icons = [{
        icon: "mdi-github",
        link: "https://github.com/MEGA-GO/Mega-GO"
    }, {
        icon: "mdi-language-python",
        link: "https://pypi.org/project/megago"
    }, {
        icon: "mdi-newspaper-variant-outline",
        link: "https://doi.org/10.1021/acs.jproteome.0c00926"
    }];
}
</script>

<style>
    .v-main__wrap {
        display: flex;
        justify-content: center;
    }

    .sublist-item {
        max-width: 85%;
        position: relative;
        left: 15%;
    }
</style>
