<template>
    <div class="page__center wide">
        <div class="page__row page__row_head" v-if="!mobile">
            <div class="page__col col__header d-flex flex-column flex-sm-row justify-content-space-between">
                <div class="mt-4 mt-sm-0">
                    <div class="page__hello h5" v-if="user" v-html="user.name+','"/>
                    <div class="page__welcome h2">Привет 👋</div>
                </div>

                <div class="mt-4 mt-sm-0">
                    <p class="mb-2">
                        <svg width="14" height="14" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle class="color" cx="7" cy="7" r="6.5" fill="#7FBA7A"/>
                        </svg>

                        <span class="color-gray ml-2 align-middle">На продвижении</span>
                    </p>
                    <p>
                        <svg width="14" height="14" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle class="color" cx="7" cy="7" r="6.5" fill="#FF4242"/>
                        </svg>

                        <span class="color-gray ml-2 align-middle">Есть заявки</span>
                    </p>
                </div>
            </div>
        </div>

        <div class="page__row" v-if="mobile">
            <div class="d-flex flex-row align-items-center justify-content-between">
                <h1>Мои треки</h1>
                <img :src="url + 'img/icon_plus_main.svg'" @click="openMusicModal" class="mb-2" />
            </div>
        </div>

        <div class="page__row" v-if="mobile">
             <div class="page__panel">
                <p>
                    <svg width="12" height="12" viewBox="0 0 12 12" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <circle class="color" cx="6" cy="6" r="5.5" fill="#7FBA7A"/>
                    </svg>

                    <span>На продвижении</span>
                </p>
                <p>
                    <svg width="12" height="12" viewBox="0 0 12 12" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <circle class="color" cx="6" cy="6" r="5.5" fill="#FF4242"/>
                    </svg>

                    <span>Есть заявки</span>
                </p>
            </div>
        </div>

        <div class="page__row page__row_border">
            <div class="page__col">
                <div class="products__grid">
                    <div class="products__item" @click="openMusicModal" v-if="!mobile">
                        <div class="products__preview new"></div>
                        <div class="products__details">
                            <div class="products__title title">Добавить трек</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>


        <div class="addtrek row bg-info m-3 rounded">
            <div class="addtrek_left col-4 text-left align-content-center m-3">
            <div class="addtrek_header">
                <h4>Загрузи свой <br> первый трек</h4>
            </div>
            <div class="addtrek_challege">
                <p>Твои будущие фанаты ждут! Жми на кнопку «добавить трек» и переходи к продвижению прямо сейчас.</p>

            </div>
            <div class="addtrek_button">
                <button type="button" class="btn btn-primary">
                    <img :src="url + 'img/add_track.svg'" @click="openMusicModal" class="w-25 h-25 mr-3"/>
                    Добавить трек
                </button>
            </div>
            </div>
            <div class="addtrek_img col-7">
                <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModal">
                    <img :src="url + 'images/shutterstock_removebg.png'" class="mb-2"/>

                </button>



                <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
                    <div class="modal-dialog">
                        <div class="modal-content">
                            <form class="col-10 m-4" action="/api/v1/add_music" method="post"     >
                                <input type="hidden" name="_token" :value="csrf">
                                <div class="d-flex  justify-content-center">
                                    <div class="col-10 text-center">
                                        <img :src="url + 'img/add_track.svg'" @click="openMusicModal" class=" "/>

                                    </div>
                                    <button type="button" class="close col-1" data-dismiss="modal" aria-label="Close">
                                        <span aria-hidden="true">&times;</span>
                                    </button>
                                </div>
                                <div class="mb-3">
                                    <label for="url" class="form-label">Ссылка на трек в тикток</label>
                                    <input type="url" class="form-control" id="url" name="url" aria-describedby="emailHelp">
                                </div>
                                <div class="mb-3">
                                    <label for="image" class="form-label">image</label>
                                    <input type="text" class="form-control" id="image" name="image" aria-describedby="emailHelp">
                                </div>
                                <div class="mb-3">
                                    <label for="title" class="form-label">Название</label>
                                    <input type="text" class="form-control" id="title" name="title">
                                </div>
                                <div class="mb-3">
                                    <label for="author" class="form-label">Исполнитель</label>
                                    <input type="text" class="form-control" id="author" name="author">
                                </div>
                                <div class="mb-3">
                                    <label for="album" class="form-label">Альбом</label>
                                    <input type="text" class="form-control" id="album" name="album">
                                </div>

                                <input type="submit" class="btn btn-primary col-12">
                            </form>
                        </div>
                    </div>
                </div>
            </div>


        </div>



        <!-- Modal -->


<!--        <form class="col-4">-->
<!--            <div class="mb-3">-->
<!--                <label for="hrefinput" class="form-label">Ссылка на трек в тикток</label>-->
<!--                <input type="email" class="form-control" id="hrefinput" aria-describedby="emailHelp">-->
<!--            </div>-->
<!--            <div class="mb-3">-->
<!--                <label for="exampleInput1" class="form-label">Название</label>-->
<!--                <input type="text" class="form-control" id="exampleInput1">-->
<!--            </div>-->
<!--            <div class="mb-3">-->
<!--                <label for="exampleInput2" class="form-label">Исполнитель</label>-->
<!--                <input type="text" class="form-control" id="exampleInput2">-->
<!--            </div>-->
<!--            <div class="mb-3">-->
<!--                <label for="exampleInput3" class="form-label">Альбом</label>-->
<!--                <input type="text" class="form-control" id="exampleInput3">-->
<!--            </div>-->

<!--            <button type="submit" class="btn btn-primary col-12">добавить</button>-->
<!--        </form>-->





        <b-modal id="music-modal" centered hide-footer>
            <div class="modal-center d-flex flex-column text-center mx-auto">
                <div class="form-block">
                    <input type="text" class="form-control" placeholder="Ссылка на звук в TikTok" v-model="val" required="" />
                    <p class="form-tip text-danger" v-if="error" v-html="error" />
                    <button class="btn btn-lg btn-primary btn-block my-4" @click="getMusic(val)" :disabled="!val" v-if="!waiting" v-html="val ? 'Найти трек' : 'Введите ссылку на трек'" />
                    <div class="loading" :class="{active: waiting}" />
                    <p class="form-tip" v-if="waiting" v-html="'Ищем трек, это займет от 5 до 10 секунд'" />
                </div>
            </div>
        </b-modal>
    </div>
</template>

<script>
    import axios from "axios"
    import {mapGetters} from "vuex";
    import { GET_MUSIC_LIST, GET_MUSIC, ADD_MUSIC } from '../api-routes';

    export default {
        components: { },
        name: "Music",

        data() {
            return {
                editing: false,
                val: this.value,
                music: null,
                error: null,
                waiting: false,
                items: null,
                csrf: document.querySelector('meta[name="csrf-token"]').getAttribute('content'),
            }
        },

        mounted() {
            this.getMusicList();
        },

        computed: {
            ...mapGetters(['user', 'userAuthorized', 'url', 'tablet', 'mobile']),
        },

        methods: {
            openMusicModal() {
                this.waiting = this.error = false;
                this.$bvModal.show('music-modal');
            },

            getMusicList() {
                axios.get(GET_MUSIC_LIST).then(response => {
                    this.items = response.data;
                });
            },

            getMusic(url) {
                this.waiting = true;
                this.error = null;

                axios.post(GET_MUSIC, {url: url}).then(response => {
                    this.waiting = false;

                    /* TO DO */
                    console.log(response);

                    this.error = null;
                }).catch(error => {
                    console.log(error);
                    this.waiting = false;
                    if(error !== undefined) {
                        this.error = 'Не удалось найти трек, попробуйте еще раз';
                    }
                });
            }
        }

    }
</script>
