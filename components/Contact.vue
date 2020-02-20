<template>
    <div id="contact__box" class="contact__box page__section">
        <div class="contact__box__inner">
            <span id="contactScroll"></span>
            <div class="contact__form__container" id="contact">
                <form id="contact__form" data-netlify="true" name="Contact" class="contact__form" action="" method="post">
                    <input type="hidden" name="Raptor-Contact" value="Contact" />
                    <div v-for="(input, index) in contact.items" :key="index">
                        <fieldset v-if="input.short_name !== 'message'">
                            <p>{{ input.text }}</p>
                            <input :aria-label="input.text" :name="input.short_name" :placeholder="input.placeholder" :type="input.field_type" :class="input.short_name">
                        </fieldset>
                        <fieldset v-else>
                            <p>{{ input.text }}</p>
                            <textarea :aria-label="input.text" :name="input.short_name" :placeholder="input.placeholder" rows="4" :type="input.field_type" :class="input.short_name"></textarea>
                        </fieldset>
                    </div>
                    <fieldset class="site__button">
                        <button class="site__button__inner contact__submit js__contact__submit" style="background-color: var(--light-orange); border: 1px solid var(--light-orange); color: rgb(255, 255, 255)" data-submit="Sending">{{ contact.button_text }}</button>
                    </fieldset>
                </form>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    computed: {
        wrapper: function () {
            return this.$store.state.theme.wrapper
        },
        sitewide: function () {
            return this.$store.state.sitewide
        }
    }
}
</script>

<style>
    .contact__form__container {
        width: 100%;
        max-width: 700px;
        margin: 20px auto;
        display: flex;
        flex-direction: column;
        flex-wrap: wrap;
        align-content: flex-start;
        justify-content: center;
        background-color: #FFF;
        border-radius: 10px;
    }
    .contact__form {
        width: 100%;
        display: flex;
        flex-direction: column;
        align-content: flex-start;
        justify-content: center;
        padding: 10px 0;
    }
    .contact__form div {
        width: 100%;
    }
    .contact__form__container fieldset {
        border: none;
    }
    .contact__form p {
        text-align: left;

        color: var(--dark-grey);
    }
    .contact__form__container input {
        border: none;
        width: 100%;
        padding: 10px 10px;
        font-size: 14px;
        border-bottom: 1px solid var(--dark-grey);
        background: transparent;
        color: var(--dark-blue);
    }
    .contact__form__container textarea {
        border: none;
        width: 100%;
        padding: 10px 10px;
        font-size: 14px;
        border-bottom: 1px solid var(--dark-grey);
        background: transparent;
        color: var(--dark-blue);
    }
    .contact__form__container input::placeholder, .contact__form__container textarea::placeholder {
        font-weight: 500;
        font-size: 13px;
    }

    #contactScroll {
        position: absolute;
        top: -70px;
        left: 0;
        width: 0;
        height: 0;
        opacity: 0;
    }
    body .contact__box {
        width: 100%;
        /* align-self: flex-end; */
        background: var(--blue);
        position: relative;
        margin: 0;
        padding-bottom: 10vh;
    }
    .contact__box__inner {
        display: flex;
        flex-direction: column;
        align-content: flex-start;
        justify-content: center;
        padding: 0 14px;
    }
    .contact__box__inner h2, .contact__box__inner p {
        color: #FFF;
        margin-left: auto;
        margin-right: auto;
    }
    .contact__box__para {
        font-size: 1.2em;
        line-height: 1.5em;
        max-width: 820px;
        margin: 30px auto 10px;
    }
    .contact__box__button {
       align-self: center;
    }
    .contact__box .page__section__header::after {
        background: #FFF !important;
    }
    /* ------------------ MEDIA QUERY ------------------ */
    @media screen and (max-width: 900px) {
        .contact__box__inner {
            padding: 0;
        }
    }
/* ------------------ MEDIA QUERY ------------------ */
@media screen and (max-width: 900px) {
    .contact__header {
        margin: 10px 0 5px;
    }
    .contact__form__container p {
        margin: 8px 0 0;
    }
    .contact__form__container input {
        padding: 6px 10px;
    }
    .contact__form__container .contact__submit {
        margin: 8px auto 0;
    }
}
/* ------------------ MEDIA QUERY ------------------ */
@media screen and (max-width: 410px) {
    .contact__header {
        margin: 6px 0 2px;
    }
    .contact__form__container p {
        margin: 4px 0 0;
    }
    .contact__form__container input {
        padding: 2px 10px;
    }
    .contact__form__container textarea {
        padding: 4px 10px;
    }
    .contact__form__container .contact__submit {
        margin: 2px auto 0;
    }
}
</style>
