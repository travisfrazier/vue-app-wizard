<template>
  <div class="form-container">
    <FormulateForm class="form" v-model="formValues" #default="{ isValid }">
      <FormulateInput
        name="GlobalName"
        label="Company Name:"
        validation="required"
        validation-name="This field"
        class="required"
      />
      <FormulateInput
        name="GlobalWebsiteUrl"
        label="Company Website URL:"
        validation="required|url"
        validation-name="This field"
        class="required"
      />
      <FormulateInput
        type="image"
        name="GlobalImage"
        label="Select your company logo to upload:"
        help="Select a png or jpg to upload"
        validation="mime:image/jpeg,image/png"
      />
      <FormulateInput
        type="group"
        name="Locales"
        :repeatable="true"
        label="Add Region:"
        add-label="+ Add Region"
        validation="required"
      >
        <div class="locale">
          <FormulateInput
            name="LocaleId"
            validation="required"
            label="Region:"
            type="select"
            :options="locales"
            placeholder="Select an option"
            validation-name="This field"
            class="required"
          />
          <FormulateInput name="LocalName" label="Regional Company Name:" />
          <FormulateInput
            type="url"
            name="LocalWebsiteUrl"
            label="Regional Website URL:"
          />
          <FormulateInput
            name="LocalPartnerCategories"
            validation="required"
            label="Classifications:"
            type="checkbox"
            :options="classifications"
            validation-name="This field"
            class="required"
          />
          <FormulateInput
            name="LocalProductCategories"
            validation="required"
            label="Product Categories:"
            type="checkbox"
            :options="categories"
            validation-name="This field"
            class="required"
          />
        </div>
      </FormulateInput>
      <FormulateInput
        :disabled="!isValid"
        @click="checkData"
        type="submit"
        label="Submit"
      />
    </FormulateForm>
  </div>
</template>

<script>
import axios from "axios";
import formData from "./../assets/formData.js";


export default {
  data() {
    return {
      formValues: {},
      locales: formData.locales,
      classifications: formData.classifications,
      categories: formData.categories,
      errorMessage: null,
    };
  },
  methods: {
    submitForm() {
      const headers = {
        "Access-Control-Allow-Origin": "*",
        "Content-Type": "Application/json",
      };
      axios
        .post("http://localhost:3000/posts", this.formValues, { headers })
        .then((res) => {
          if (res.status == "201" || res.status == "200") {
            this.$router.push("/success");
          }
        })
        .catch((error) => {
          // error.response.status Check status code
          this.errorMessage = error.message;
          console.error("There was an error!", error);
        });
    },
    checkData() {
      this.convertToNum();

      if (this.formValues.GlobalImage) {
        const image = this.formValues.GlobalImage.files[0].previewData;
        this.resizeImage(image, 223, 125).then((value) => {
          this.formValues.GlobalImage = value;
          this.submitForm();
        });
      } else {
        this.submitForm();
      }
    },
    convertToNum() {
      const dataToConvert = this.formValues.Locales;

      dataToConvert.forEach(function (element, index, dataToConvert) {
        dataToConvert[index].LocaleId = parseInt(dataToConvert[index].LocaleId);

        dataToConvert[index].LocalPartnerCategories.forEach(function (
          element,
          index,
          LocalPartnerCategories
        ) {
          LocalPartnerCategories[index] = parseInt(
            LocalPartnerCategories[index]
          );
        });

        dataToConvert[index].LocalProductCategories.forEach(function (
          element,
          index,
          LocalProductCategories
        ) {
          LocalProductCategories[index] = parseInt(
            LocalProductCategories[index]
          );
        });
      });
    },
    resizeImage(base64Str, maxWidth = 400, maxHeight = 350) {
      return new Promise((resolve) => {
        let img = new Image();
        img.src = base64Str;
        img.onload = () => {
          let canvas = document.createElement("canvas");
          const MAX_WIDTH = maxWidth;
          const MAX_HEIGHT = maxHeight;
          let width = img.width;
          let height = img.height;

          if (width > height) {
            if (width > MAX_WIDTH) {
              height *= MAX_WIDTH / width;
              width = MAX_WIDTH;
            }
          } else {
            if (height > MAX_HEIGHT) {
              width *= MAX_HEIGHT / height;
              height = MAX_HEIGHT;
            }
          }
          canvas.width = width;
          canvas.height = height;
          let ctx = canvas.getContext("2d");
          ctx.drawImage(img, 0, 0, width, height);
          resolve(canvas.toDataURL());
        };
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.form-item-group {
  display: flex;
  justify-content: space-between;
  gap: 35px;
}
.form-container {
  width: 100%;
}
.form {
  width: 100%;
}
span {
  font-size: 12px;
  font-style: italic;
  display: block;
  text-align: right;
}
</style>