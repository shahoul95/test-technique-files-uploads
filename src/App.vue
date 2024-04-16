<template>
  <div class="main">
    <UploadFile @form-value="getFormValue" />
    <div class="mt-5 m-4" ref="table"></div>
  </div>
</template>

<script>
import "tabulator-tables/dist/css/tabulator.min.css";
import * as Tabulator from "tabulator-tables";
import UploadFile from "./components/UploadFile.vue";

export default {
  components: {
    UploadFile,
  },
  data() {
    return {
      tableInstance: null,
    };
  },
  mounted() {
    const tabledata = [
      {
        name: "Fichier1",
        libelle: "Label1",
        categorie: "Document marketing",
        comments: "Commentaire1",
        dateDeposite: "2024-04-10",
        create: "Jean Dupont",
        destinataire: "Destinataire1",
        status: "En attente",
        dateDownload: "2024-04-12",
        fileSize: "2.5 MB",
        recepFile: "Oui",
        limitationStockage: "Non",
        fileType: "Type1",
        file: "",
      },
      {
        name: "Fichier2",
        libelle: "Label2",
        categorie: "Catégorie2",
        comments: "Commentaire2",
        dateDeposite: "2024-04-10",
        create: "Jean Dupont",
        destinataire: "Destinataire2",
        status: "En attente",
        dateDownload: "2024-04-12",
        fileSize: "2.5 MB",
        recepFile: "Oui",
        limitationStockage: "Non",
        fileType: "Type2",
        file: "",
      },
      {
        name: "Fichier3",
        libelle: "Label3",
        categorie: "Document marketing",
        comments: "Commentaire3",
        dateDeposite: "2024-04-10",
        create: "Jean Dupont",
        destinataire: "Destinataire3",
        status: "En attente",
        dateDownload: "2024-04-12",
        fileSize: "2.5 MB",
        recepFile: "Oui",
        limitationStockage: "Non",
        fileType: "Type1",
        file: "",
      },
      {
        name: "Fichier4",
        libelle: "Label4",
        categorie: "Catégorie4",
        comments: "Commentaire4",
        dateDeposite: "2024-04-10",
        create: "Jean Dupont",
        destinataire: "Destinataire4",
        status: "En attente",
        dateDownload: "2024-04-12",
        fileSize: "2.5 MB",
        recepFile: "Oui",
        limitationStockage: "Non",
        fileType: "Type2",
        file: "",
      },
      {
        name: "Fichier5",
        libelle: "Label5",
        categorie: "Document marketing",
        comments: "Commentaire5",
        dateDeposite: "2024-04-10",
        create: "Jean Dupont",
        destinataire: "Destinataire5",
        status: "En attente",
        dateDownload: "2024-04-12",
        fileSize: "2.5 MB",
        recepFile: "Oui",
        limitationStockage: "Non",
        fileType: "Type1",
        file: "",
      },
      {
        name: "Fichier6",
        libelle: "Label6",
        categorie: "Catégorie6",
        comments: "Commentaire6",
        dateDeposite: "2024-04-10",
        create: "Jean Dupont",
        destinataire: "Destinataire2",
        status: "En attente",
        dateDownload: "2024-04-12",
        fileSize: "2.5 MB",
        recepFile: "Oui",
        limitationStockage: "Non",
        fileType: "Type2",
        file: "",
      },
      {
        name: "Fichier7",
        libelle: "Label7",
        categorie: "Document marketing",
        comments: "Commentaire7",
        dateDeposite: "2024-04-10",
        create: "Jean Dupont",
        destinataire: "Destinataire7",
        status: "En attente",
        dateDownload: "2024-04-12",
        fileSize: "2.5 MB",
        recepFile: "Oui",
        limitationStockage: "Non",
        fileType: "Type1",
        file: "",
      },
      {
        name: "Fichier8",
        libelle: "Label8",
        categorie: "Catégorie8",
        comments: "Commentaire8",
        dateDeposite: "2024-04-10",
        create: "Jean Dupont",
        destinataire: "Destinataire8",
        status: "En attente",
        dateDownload: "2024-04-12",
        fileSize: "2.5 MB",
        recepFile: "Oui",
        limitationStockage: "Non",
        fileType: "Type2",
        file: "",
      },
      {
        name: "Fichier9",
        libelle: "Label9",
        categorie: "Document marketing",
        comments: "Commentaire9",
        dateDeposite: "2024-04-10",
        create: "Jean Dupont",
        destinataire: "Destinataire9",
        status: "En attente",
        dateDownload: "2024-04-12",
        fileSize: "2.5 MB",
        recepFile: "Oui",
        limitationStockage: "Non",
        fileType: "Type9",
        file: "",
      },
      {
        name: "Fichier10",
        libelle: "Labe10",
        categorie: "Catégorie10",
        comments: "Commentaire10",
        dateDeposite: "2024-04-10",
        create: "Jean Dupont",
        destinataire: "Destinataire10",
        status: "En attente",
        dateDownload: "2024-04-12",
        fileSize: "2.5 MB",
        recepFile: "Oui",
        limitationStockage: "Non",
        fileType: "Type2",
        file: "",
      },
    ];

    this.tableInstance = new Tabulator(this.$refs.table, {
      data: tabledata,
      layout: "fitColumns",
      responsiveLayout: "hide",
      tooltips: true,
      addRowPos: "top",
      history: true,
      pagination: "local",
      paginationSize: 4,
      movableColumns: true,
      resizableRows: true,
      columns: [
        { title: "Nom", field: "name", width: 150 },
        { title: "Libellé", field: "libelle" },
        { title: "Catégorie", field: "categorie" },
        { title: "Commentaire", field: "comments" },
        {
          title: "Date de Dépôt",
          field: "dateDeposite",
          hozAlign: "center",
          sorter: "date",
        },
        { title: "Créateur", field: "create" },
        { title: "Destinataire", field: "destinataire" },
        { title: "Statut", field: "status" },
        {
          title: "Date de Téléchargement",
          field: "dateDownload",
          hozAlign: "center",
          sorter: "date",
        },
        { title: "Taille du Fichier", field: "fileSize" },
        { title: "Réception du Fichier", field: "recepFile" },
        { title: "Limitation de Stockage", field: "limitationStockage" },
        { title: "Type de Fichier", field: "fileType" },
        { title: "File", field: "file", visible: false },
        {
          title: "Télécharger",
          field: "download",
          formatter: this.downloadButtonFormatter,
        },
        {
          title: "Supprimer",
          field: "delete",
          formatter: this.deleteButtonFormatter,
        },
      ],
    });
  },
  methods: {
    getFormValue(form) {
      const { category, recipient, label, comment, file } = form;
      const now = new Date();
      const day = String(now.getDate()).padStart(2, "0");
      const month = String(now.getMonth() + 1).padStart(2, "0");
      const year = now.getFullYear();
      const hours = String(now.getHours()).padStart(2, "0");
      const minutes = String(now.getMinutes()).padStart(2, "0");
      const seconds = String(now.getSeconds()).padStart(2, "0");
      const dateNow = year + "-" + month + "-" + day;
      const timeNow = hours + ":" + minutes + ":" + seconds;

      const taille_octets = file.size;
      const taille_ko = taille_octets / 1024;
      const filzeAfterTwoDo = taille_ko.toFixed(2);

      const forms = {
        name: file.name,
        libelle: label,
        categorie: category,
        comments: comment,
        dateDeposite: dateNow + " " + timeNow,
        create: "Jean Dupont",
        destinataire: recipient,
        status: "En attente",
        dateDownload: dateNow + " " + timeNow,
        fileSize: filzeAfterTwoDo + "ko",
        recepFile: "Oui",
        limitationStockage: "Non",
        fileType: file.type,
        file: file,
      };
      this.tableInstance.addRow(forms);
    },
    downloadButtonFormatter: function (cell) {
      const fileData = cell.getRow().getData();
      const downloadBtn = document.createElement("button");
      downloadBtn.innerHTML = "Télécharger";
      if (fileData.file) {
        downloadBtn.addEventListener("click", function () {
          const url = URL.createObjectURL(fileData.file);
          const now = new Date();
          const day = String(now.getDate()).padStart(2, "0");
          const month = String(now.getMonth() + 1).padStart(2, "0");
          const year = now.getFullYear();
          const dateNow = year + "-" + month + "-" + day;
          fileData.dateDownload = dateNow;

          const tableData = cell.getRow().getTable().getData();
          const updatedTableData = tableData.map((row) => {
            if (row === fileData) {
              return fileData;
            } else {
              return row;
            }
          });

          cell.getRow().getTable().setData(updatedTableData);

          const lienTelechargement = document.createElement("a");
          lienTelechargement.href = url;
          lienTelechargement.download = fileData.name || "fichier";
          lienTelechargement.textContent = "Télécharger";
          document.body.appendChild(lienTelechargement);

          lienTelechargement.click();
        });
      }

      return downloadBtn;
    },
    deleteButtonFormatter: function (cell) {
      var fileData = cell.getRow().getData();
      var downloadBtn = document.createElement("button");
      downloadBtn.innerHTML = "Supprimer";

      downloadBtn.addEventListener("click", function () {
        const lienTelechargement = document.createElement("a");
        lienTelechargement.download = fileData.name || "fichier";
        lienTelechargement.textContent = "Supprimer";
        document.body.appendChild(lienTelechargement);
        lienTelechargement.click();
        cell.getRow().delete();
      });

      return downloadBtn;
    },
  },
};
</script>

<style scoped>
.tabulator {
  border: 1px solid #596aee;
  background: white;
  border-radius: 10px;
  font-size: 14px;
  overflow: hidden;
  position: relative;
  text-align: left;
  transform: translateZ(0);
}
.main {
  background-color: #f0ecec;
  min-height: 100vh;
}
</style>
