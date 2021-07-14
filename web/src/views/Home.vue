<template>
    <v-container fluid>
        <div>
            <div class="text-h3">Welcome</div>
            <p class="text-body-1">
                The MegaGO project aims to provide users with a measure that indicates how similar two sets of GO terms
                are to each other. Head over <router-link to="/analysis">to the analysis page</router-link> to get
                started. This is the web based version of our project that computes the similarity score for your GO
                terms of choice remotely in our cloud. If you however want to compute similarities in bulk or offline,
                you can download the megago package from <a href="https://pypi.org/project/megago/">PyPi</a> by
                executing `pip install megago`.
            </p>
            <p class="text-body-1">
                MegaGO is completely open source and can be found on GitHub. All pull requests or suggestions are
                welcome. If you encounter a problem while using MegaGO you are welcome to open
                <a href="https://github.com/MEGA-GO/Mega-GO/issues">a new issue</a> in our repository and we'll do our
                best to take a look and resolve the issue as soon as possible. Make sure to check that a similar issue
                has not been reported before.
            </p>
            <p class="text-body-1">
                If you decide to use this tool, please cite <a href="https://doi.org/10.1021/acs.jproteome.0c00926">Verschaffelt P, Van Den Bossche T, et al.</a>.
            </p>
            <div class="d-flex justify-center align-center">
                <v-btn x-large color="primary" to="/analysis">
                    <v-icon x-large class="mr-2">mdi-play-circle</v-icon>
                    Start analysis
                </v-btn>
            </div>
        </div>
    </v-container>
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";

@Component
export default class Home extends Vue {

}
</script>

<style scoped>

</style>
