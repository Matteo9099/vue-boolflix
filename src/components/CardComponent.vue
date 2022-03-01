<template>
  <div class="card d-flex justify-content-end" :style="{ 'background-image': `url(${posterUrl})` }">

    <div class="hover-description h-100">
        <div class="title-container">
            <p class="title mb-1">{{ item.title || item.name }}</p>
            <p class="original-title">{{ item.original_title || item.original_name }}</p>
        </div>

        <div class="flag-rating-container">
            <img class="flag" v-if="languages" :src="langSrc" :alt="item.original_language"/>
            <span v-else>{{ item.original_language }}</span>
            <div class="star-rating">
              <i v-for="i in 5" :key="i" :class="iconStar(starVote, i)" class="fa-star"></i>
            </div>
        </div>

        <div class="overview-container">
            <span v-if="item.overview">Overview:</span>
            <p class="overview">{{ item.overview }}</p>
        </div>
    </div>

  </div>
</template>

<script>
export default {
  name: "CardComponents",
  props: ["item"],
  data() {
    return {
      langs: ["it", "en", "es", "fr", "de", "pt", "ja"],
      basePosterUrl: "https://image.tmdb.org/t/p/",
    };
  },
  methods: {
    // creazione metodo che confronta i voti 
    iconStar(vote, index) {
      return (vote >= index) ? "fa-solid" : "fa-regular";
    },
  },
  computed: {
    // arrotondamento numeri
    starVote() {
      return Math.ceil(this.item.vote_average / 2);
    },
    posterUrl() {
      if (this.item.poster_path != null) {
        return `${this.basePosterUrl}w342${this.item.poster_path}`;
      }
      return `https://cloud.filmfed.com/defaults/movie-poster/m_movie_poster_default.png`;
    },
    langSrc() {
      return require(`../assets/img/${this.item.original_language}.png`);
    },
    languages() {
      return this.langs.includes(this.item.original_language);
    },
  },
};
</script>

<style scoped lang="scss">
@import "../assets/style/vars.scss";

    .card {
        display: inline-block;
        margin: 30px;
        height: 450px;
        width: 300px;
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;
        border-radius: 15px;
        border: 1px solid rgb(247, 245, 245);

        img {
            object-fit: cover;
            border-radius: 15px;
        }

        &:hover {
            opacity: 1;
            transition: 0.5s;
            transform: rotateY(180deg);
        }

        .hover-description {
                display: flex;
                justify-content: space-between;
                flex-direction: column;
                align-items: center;
                padding: 15px;
                text-align: center;
                background-color: #000;
                border-radius: 15px;
                opacity: 0;

             ::-webkit-scrollbar {
                width: 7px;
              }

            &:hover{
              opacity: 1;
              transform: rotateY(180deg);
            }

            .title {
                font-size: 1.5rem;
                font-weight: bold;
                color: $colorTitleCard;

            }

            .original-title {
                font-size: 0.9rem;
                color: rgb(245, 132, 67);
            }

            .flag {
                width: 50px;
                height: 30px;
                margin-bottom: 10px;
            }

            .star-rating {
                display: block;
                color: yellow;
            }

            span{
                color: rgb(245, 132, 67);
            }

            .overview {
                height: 180px;
                overflow: auto;
                text-align: left;
                margin-top: 10px;
                padding-left: 15px;
                padding-right: 15px;
                color: $colorTitleCard;
            }
            
            ::-webkit-scrollbar-track {
                box-shadow: inset 0 0 3px rgb(252, 0, 0);
                border-radius: 10px;
            }

            ::-webkit-scrollbar-thumb {
                background: #f5a938;
                border-radius: 10px;
            }

    }
}
</style>