<!--
    Copyright 2020 Phil Schatzmann

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <https://www.gnu.org/licenses/>.
-->

<template>
    <v-container fluid>
            <v-row>
                <v-col  v-for="item in $store.state.genres" :key="item.name" >
                    <v-hover  v-slot:default="{ hover }" close-delay="200">
                        <v-card outlined tiled class="mx-auto" max-width="200px" :elevation="hover ? 16 : 2" @click.native="doSelect(item.name)">

                            <v-img
                                :src="item.imageUrl"
                                class="white--text align-end"
                                height="200px"
                                width="200px">

                            </v-img>
                            <v-card-text> 
                                {{ item.name }}
                             </v-card-text>
                                                
                        </v-card>
                    </v-hover>
                </v-col>
            </v-row>
    </v-container>
</template>

<script>

export default {
    methods: {
        doSelect: function (search) {
            this.$router.push({ path: '/genres/'+search.toLowerCase() })
        }
    },

    mounted() {
        this.$store.dispatch('setupGenres')
    }
  }

</script>

<style>
    .v-card {
        cursor: pointer;
    }

</style>