<template>
  <div id="app">
    <h2 class="text-center text-3xl p-7">UpVote!</h2>
    <div class="flex flex-wrap justify-center gap-3">
      <Upvote
        v-for="submission in sortedSubmissions"
        :key="submission.id"
        v-bind:id="submission.id"
        :title="submission.title"
        :avatar="submission.avatar"
        :description="submission.description"
        :votes="submission.votes"
        :submissionImage="submission.submissionImage"
        :upvote="upvote"
      />
    </div>
  </div>
</template>

<script>
import Upvote from "./components/Upvote.vue"
import { submissions } from "./data/seed"

export default {
  name: "App",
  components: {
    Upvote,
  },
  data() {
    return {
      submissions,
    }
  },
  computed: {
    sortedSubmissions () {
      return [...this.submissions].sort((a, b) => {
        return b.votes - a.votes
      });
    }
  },
  methods: {
    upvote(submissionId) {
      const submission = this.submissions.find(
        submission => submission.id === submissionId
      );
      submission.votes++;
    },
  }
}
</script>

<style></style>
