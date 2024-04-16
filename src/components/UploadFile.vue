<template>
  <div class="d-flex justify-content-center">
    <div
      class="file-upload bg-white mt-4"
      @dragenter.prevent="handleDragEnter"
      @dragover.prevent="handleDragOver"
      @drop.prevent="handleFileDrop"
    >
      <div class="text-center mt-3">
        <label for="file-upload" class="buttonCustom text-white p-2">
          Télécharger</label
        >
        <input
          id="file-upload"
          type="file"
          style="visibility: hidden"
          @change="handleFileUpload"
        />
        <img :src="svg" height="150" alt="Mon SVG" />
      </div>
      <div v-if="isFileUploaded" class="text-center">
        Fichier téléversé avec succès !
      </div>
      <p class="text-center">Glisser ou déposer</p>
    </div>

    <div class="bg-white mt-4 file-upload p-4 align-item-center">
      <div class="form-group">
        <label for="label">Libellé:</label>
        <input
          type="text"
          v-model="label"
          id="label"
          class="form-control inputFile"
        />
      </div>

      <div class="form-group">
        <label for="category">Catégorie:</label>
        <select v-model="category" id="category" class="form-control inputFile">
          <option value="" disabled selected>Sélectionnez une catégorie</option>
          <option value="Proposition commerciale">
            Proposition commerciale
          </option>
          <option value="Présentation">Présentation</option>
          <option value="Document marketing">Document marketing</option>
          <option value="Réponse AO">Réponse AO</option>
          <option value="Data">Data</option>
          <option value="Signature du contrat">Signature du contrat</option>
          <option value="Formulaire d'engagement">
            Formulaire d'engagement
          </option>
          <option value="Devis">Devis</option>
          <option value="Renouvellement de contrat">
            Renouvellement de contrat
          </option>
          <option value="Rapport">Rapport</option>
          <option value="Proposition de renouvellement">
            Proposition de renouvellement
          </option>
          <option value="Autre">Autre</option>
        </select>
      </div>

      <div class="form-group">
        <label for="recipient">Destinataire:</label>
        <input
          type="text"
          v-model="recipient"
          id="recipient"
          class="form-control inputFile"
        />
      </div>

      <div class="form-group">
        <label for="comment">Commentaire:</label>
        <textarea
          v-model="comment"
          id="comment"
          class="form-control inputFile"
        ></textarea>
      </div>

      <div class="form-group text-center">
        <button @click="submitForm" class="btn btn-primary mt-4 buttonCustom">
          Ajouter
        </button>
      </div>

      <div class="form-group pt-4" v-if="validationError">
        <div class="alert alert-danger">{{ validationError }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import svg from "../assets/file.svg";
export default {
  name: "UploadFile",
  data() {
    return {
      svg: svg,
      label: "",
      category: "",
      recipient: "",
      comment: "",
      isFileUploaded: false,
      fileUpload: "",
      validationError: "",
    };
  },
  methods: {
    handleFileUpload(event) {
      const file = event.target.files[0];
      if (file) {
        // Traiter le fichier ici (par exemple, le télécharger sur un serveur)
        this.isFileUploaded = true;
        this.fileUpload = file;
      }
    },
    handleDragEnter(event) {
      event.preventDefault();
    },
    handleDragOver(event) {
      event.preventDefault();
    },
    handleFileDrop(event) {
      event.preventDefault();
      const file = event.dataTransfer.files[0];
      if (file) {
        this.isFileUploaded = true;
        this.fileUpload = file;
      }
    },
    submitForm() {
      if (
        !this.label ||
        !this.category ||
        !this.recipient ||
        !this.comment ||
        !this.isFileUploaded
      ) {
        this.validationError =
          "Veuillez remplir tous les champs et téléverser un fichier.";
        return;
      }


      const formData = {
        label: this.label,
        category: this.category,
        recipient: this.recipient,
        comment: this.comment,
        file: this.fileUpload,
      };
      this.$emit("formValue", formData);

 
      this.validationError = "";
      this.label = "";
      this.category = "";
      this.recipient = "";
      this.comment = "";
      this.isFileUploaded = false;
    },
  },
};
</script>

<style scoped>
.file-upload {
  border-radius: 10px;
  height: 100%;
  width: 30%;
  margin: 30px;
}
.inputFile {
  border-radius: 30px;
  border-color: #596aee;
  height: 40px;
}
.buttonCustom {
  border-radius: 10px;
  background-color: #596aee;
  width: 100px;
}
</style>
