<template>
    <article id="lyrics">
        <div class="content">
            <div v-if="lyrics">{{{ lyrics }}}</div>
            <p class="none" v-else>No lyrics found. Are you not listening to Bach?</p>
        </div>
    </article>
</template>

<script>
    import songStore from '../../../stores/song';

    export default {
        replace: false,

        data() {
            return {
                lyrics: '',
            };
        },

        methods: {
            resetState() {
                this.lyrics = '';
            },
        },

        events: {
            'song:info-loaded': function (song) {
                this.lyrics = song.lyrics;
            },
        },
    };
</script>

<style lang="sass">
    @import "resources/assets/sass/partials/_vars.scss";
    @import "resources/assets/sass/partials/_mixins.scss";
</style>
