<template>
  <article class="flex gap-3 border p-5 justify-between" :class="{ 'border-blue-500': votes >= 20 }">
    <figure>
      <img class="w-[64px]" :src="submissionImage" />
    </figure>
      <div class="w-full">
        <p>
          <strong>
            <a href="#">{{ title }}</a>
            <span>{{ id }}</span>
          </strong>
          <br />
          {{ description }}
          <br />
          <small class="flex gap-3">
            Submitted by:
            <img class="w-[24px] rounded-xl" :src="avatar" />
          </small>
        </p>
      </div>
    <div class="">
      <span @click="upvote(id)">
        <i class="fa fa-chevron-up"></i>
        <strong>{{ votes }}</strong>
      </span>
    </div>
  </article>
</template>

<script>
export default {
  name: "Upvote",
  props: {
    id: Number,
    title: String,
    description: String,
    votes: Number,
    avatar: String,
    submissionImage: String,
    upvote: Function,
  },
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
article {
  width: 50%;
  min-width: 400px;
}
</style>
