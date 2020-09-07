<template>
  <div
    v-if="index <= (isMember ? itemlenght : 999)"
    class="col-lg-12 p-3"
    @click="handleClickCard(law.law_no)"
  >
    <div
      class="row p-3 m-2 bg-white shadow-sm rounded"
      style="cursor: pointer;"
    >
      <div class="col-lg-2">
        <div class="text-center">
          <img class="w-75" src="http://via.placeholder.com/300x300" alt />
        </div>
      </div>
      <div class="col-lg-10">
        <div class="col-lg-12">
          <p>
            <b>{{ law.law_content_1 }}</b>
          </p>
          <br />
        </div>
        <div class="row">
          <div class="col-lg-6">
            <a>
              <span class="text-info">
                <b>{{ law.proposer_name }}</b>
              </span>
            </a>
          </div>
          <div class="col-lg-6">
            <span class="text-secondary">
              {{ law.proposed_date }}
            </span>
            <span class="text-right">
              {{ law.no_of_supporter }}/{{ law.law_status == 1 ? 20 : 10 }}
              คน
            </span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      itemlenght: 4,
    }
  },
  props: {
    law: { type: Object },
    index: { type: Number },
    isMember: { type: Boolean },
  },
  methods: {
    handleClickCard(id) {
      this.$emit('clickCardInitLaw', id)
    },
  },
}
</script>

<style></style>
