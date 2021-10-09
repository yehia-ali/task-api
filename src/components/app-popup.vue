<template>
  <div
    class="modal fade"
    id="AddReview"
    tabindex="-1"
    aria-labelledby="AddReviewLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="AddReviewLabel">Add Review</h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <form>
            <div class="mb-3">
              <label for="reviewTitle" class="form-label text-uppercase"
                >Rating</label
              >
              <star-rating
                v-model="rating"
                v-bind:star-size="20"
                v-bind:increment="1"
                v-bind:show-rating="false"
              ></star-rating>
            </div>

            <div class="mb-3">
              <label for="reviewTitle" class="form-label text-uppercase"
                >Review Title</label
              >
              <input type="text" class="form-control" id="reviewTitle" />
            </div>
            <div class="mb-3">
              <label for="reviewDetails" class="form-label text-uppercase"
                >Review Details</label
              >
              <textarea
                class="form-control"
                id="reviewDetails"
                style="height: 100px"
              ></textarea>
            </div>
          </form>
        </div>
        <div class="modal-footer">
          <button type="submit" class="btn btn-green">Add Review</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import StarRating from "vue-star-rating";

export default {
  components: {
    StarRating,
  },
  methods: {
    setRating(rating) {
      this.rating = rating;
    },
  },

  data() {
    return {
      rating: 0,
    };
  },
};
</script>
