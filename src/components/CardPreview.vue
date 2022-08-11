<template>
  <v-container>
    <h4 class="text-right mb-4">HCARD PREVIEW</h4>
    <div class="card-preview">
      <div class="card-header">
        <div class="header">
          <h2>{{ gname }} {{ sname }}</h2>
        </div>
      </div>
      <v-img class="image" :src="imageUrl" />
      <div class="card-body">
        <div class="field label">Email</div>
        <div class="field">
          {{ email }}
        </div>
        <div class="field label">Phone</div>
        <div class="field">
          {{ phone }}
        </div>
        <div class="field label">Address</div>
        <div class="field">{{ housename }} {{ street }} {{ suburb }} {{ state }}</div>
        <div class="field label">Postcode</div>
        <div class="field">
          {{ postcode }}
        </div>
        <div class="field label">Country</div>
        <div class="field">
          {{ country }}
        </div>
      </div>
    </div>
  </v-container>
</template>

<script>
export default {
  name: "CardPreview",
  props: [
    "gname",
    "sname",
    "email",
    "phone",
    "housename",
    "street",
    "suburb",
    "state",
    "postcode",
    "country",
    "imageUrl",
  ],
};
</script>
<style scoped>
h2 {
  display: flex;
  align-items: center;
  height: 100%;
  padding: 20px;
  color: #fff;
}
h4 {
  text-transform: uppercase;
  letter-spacing: 0.5px;
}
</style>
