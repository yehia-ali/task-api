<template>
  <div>
    <div class="profile-card" v-for="review of reviews" :key="review.id">
      <div class="profile-img">
        <img :src="review.picture" alt="profile card" />
      </div>

      <div class="profile-content text-center">
        <h5>{{ review.category }}</h5>
        <p class="text-gray" v-if="review.date">
          {{ moment(review.date).format("D MMM YYYY") }}
        </p>
        <h2 class="text-capitalize">{{ review.userComment }}</h2>

        <div class="card-rating">
          <div
            class="card d-inline-block px-3 py-2 thumbs-down border-0 rounded-0"
            v-if="review.starRating <= 4"
          >
            <i class="fas fa-thumbs-down"></i>
          </div>

          <div
            class="card d-inline-block px-3 py-2 thumbs-up border-0 rounded-0"
            v-if="review.starRating >= 4"
          >
            <i class="fas fa-thumbs-up"></i>
          </div>

          <div class="card d-inline-block p-3 py-2 border-start-0 rounded-0">
            <star-rating
              v-bind:max="review.userComment"
              v-bind:star-size="25"
              v-model:rating="review.starRating"
              read-only
            ></star-rating>
          </div>
        </div>

        <p class="text-start">
          {{ review.Comment }}
        </p>
        <div
          class="reply"
          v-for="(reply, index) of review.replies"
          :key="index"
        >
          <span></span>
          <p class="text-start">
            {{ reply }}
          </p>
        </div>
        <div class="text-center">
          <button
            @click="isShow = !isShow"
            type="button"
            class="btn btn-green text-uppercase"
          >
            Add Comment
          </button>
        </div>
      </div>
      <div class="profile-comment" v-show="isShow">
        <div class="mb-3">
          <label
            for="reviewDetails"
            class="form-label text-uppercase text-start"
            >Add Comment</label
          >
          <textarea
            class="form-control"
            id="reviewDetails"
            style="height: 150px"
            v-model="newComment"
            @keyup.enter="addComment(review, newComment)"
          ></textarea>
        </div>
      </div>
    </div>
  </div>
</template>
<style lang="scss">
.profile-card {
  width: 100%;
  min-height: 200px;
  margin: auto;
  box-shadow: 0px 0px 5px 0 rgba(13, 28, 39, 0.6);
  background: #fff;
  border-radius: 6px;
  max-width: 62vw;
  position: relative;
  top: -130px;
  margin-bottom: 80px;
  @media screen and (max-width: 576px) {
    max-width: 100vw;
    margin-bottom: 100px;
  }

  h5 {
    color: #5ba2d2;
  }
  p {
    &.text-gray {
      color: #8d8d8d;
    }
  }
  .card-rating {
    margin-bottom: 10px;
    @media screen and (max-width: 576px) {
      text-align: center;
    }
    .thumbs-up {
      background: #00b800;
      color: #fff;
      border: 1px solid #00b800;
    }
    .thumbs-down {
      background: #ff0000;
      color: #fff;
      border: 1px solid #ff0000;
    }
    i {
      padding: 5px 0 8px;
    }
    .card-rating {
      @media screen and (max-width: 576px) {
        text-align: left;
      }

      .vue-star-rating-rating-text {
        padding-left: 30px;
        @media screen and (max-width: 576px) {
          padding-left: 15px;
        }
      }
    }
  }

  .profile-img {
    width: 80px;
    height: 80px;
    transform: translate(28vw, -60%);
    border-radius: 50%;
    position: absolute;
    z-index: 4;
    @media screen and (max-width: 576px) {
      transform: translate(36vw, -60%);
    }
    img {
      display: block;
      width: 100%;
      height: 100%;
      object-fit: cover;
      border-radius: 50%;
    }
  }

  .profile-content {
    padding: 40px 80px;
    @media screen and (max-width: 576px) {
      padding: 60px 35px 40px;
    }
  }
  .profile-comment {
    padding: 0 80px 40px;
    @media screen and (max-width: 576px) {
      padding: 0 42px 30px;
    }
  }
  .reply {
    span {
      width: 0;
      height: 0;
      border-left: 25px solid transparent;
      border-right: 25px solid transparent;
      border-bottom: 25px solid #ebf0f2;
    }
    p {
      background: #ebf0f2;
      padding: 20px;
      margin: 10px 0;
    }
  }
}
</style>

<script>
import moment from "moment";
import StarRating from "vue-star-rating";
import axios from "axios";
const baseUrl = " http://localhost:3000/reviews";

export default {
  components: {
    StarRating,
  },
  state: {
    reviews: [],
  },

  data: function() {
    return {
      authorName: "yehia ali",
      picture: "https://randomuser.me/api/portraits/men/2.jpg",
      isShow: false,
      reviews: [],
      rating: "",
      newComment: "",
    };
  },

  mounted() {
    this.getreviews();
  },

  methods: {
    moment: function(date) {
      return moment(date);
    },

    getreviews: function() {
      axios.get(baseUrl).then((res) => {
        this.reviews = res.data;
      });
    },
    async addComment(rev, newComm) {
      rev.replies.push(newComm);
      this.newComment = "";
    },
  },
};
</script>
