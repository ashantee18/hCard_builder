<template>
  <v-row no-gutters>
    <v-col
      v-for="n in 2"
      :key="n"
      :cols="n === 1 ? 12 : 12"
      :md="n === 1 ? 6 : 6"
      v-bind:class="{ hcard: n === 2 }"
    >
      <v-card flat tile class="no-border pa-4">
        <div v-if="n === 1">
          <form>
            <h1>hCard Builder</h1>
            <h4 class="mt-4">PERSONAL DETAILS</h4>
            <v-divider class="mb-4" />
            <v-row class="text-center">
              <v-col cols="12" md="6">
                <v-text-field v-model="gname" label="Given Name"></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-text-field v-model="sname" label="Surname"></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-text-field v-model="email" label="Email"></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-text-field v-model="phone" label="Phone"></v-text-field>
              </v-col>
              <v-col cols="12">
                <h4 class="mt-4 text-left">ADDRESS</h4>
                <v-divider class="mb-4" />
              </v-col>
              <v-col cols="12" md="6">
                <v-text-field v-model="housename" label="House name or #"></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-text-field v-model="street" label="Street"></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-text-field v-model="suburb" label="Suburb"></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-text-field v-model="state" label="State"></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-text-field v-model="postcode" label="Post Code"></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-text-field v-model="country" label="Country"></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-file-input
                  v-model="image"
                  type="file"
                  class="input"
                  outlined
                  dense
                  @change="onFileChange"
                  accept="image/png, image/jpeg, image/bmp"
                  placeholder="Pick an avatar"
                  prepend-icon="mdi-camera"
                  label="Avatar"
                />
              </v-col>
              <v-col cols="12" md="6">
                <v-btn @click="clear"> Create hCard </v-btn>
              </v-col>
            </v-row>
          </form>
        </div>
        <CardPreview
          v-else
          :gname="gname"
          :sname="sname"
          :email="email"
          :phone="phone"
          :housename="housename"
          :street="street"
          :suburb="suburb"
          :state="state"
          :postcode="postcode"
          :country="country"
          :imageUrl="imageUrl"
        />
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import CardPreview from "./CardPreview";
export default {
  name: "CardForm",
  components: { CardPreview },
  data() {
    return {
      gname: "",
      sname: "",
      email: "",
      phone: "",
      housename: "",
      street: "",
      suburb: "",
      state: "",
      postcode: "",
      country: "",
      image: undefined,
      imageUrl: "",
    };
  },
  methods: {
    createImage(file) {
      const reader = new FileReader();

      reader.onload = (e) => {
        this.imageUrl = e.target.result;
      };
      reader.readAsDataURL(file);
    },
    onFileChange(file) {
      if (!file) {
        return;
      }
      this.createImage(file);
    },
  },
};
</script>
