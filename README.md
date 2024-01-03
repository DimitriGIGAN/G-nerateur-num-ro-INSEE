<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Générateur de numéro de sécurité sociale</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      background-color: #f4f4f4;
      margin: 0;
      padding: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }

    form {
      background-color: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }

    h1 {
      text-align: center;
      color: #333;
    }

    label {
      display: block;
      margin-bottom: 8px;
      color: #555;
    }

    input {
      width: 100%;
      padding: 8px;
      margin-bottom: 16px;
      box-sizing: border-box;
    }

    input[type="button"] {
      background-color: #3498db;
      color: #fff;
      border: none;
      padding: 10px;
      cursor: pointer;
      border-radius: 4px;
    }

    input[type="button"]:hover {
      background-color: #2980b9;
    }

    #numero_securite_sociale {
      margin-top: 20px;
      font-weight: bold;
      color: #27ae60;
    }

    .error {
      color: #e74c3c;
      margin-top: 5px;
    }
  </style>
</head>
<body>

  <form action="#" method="post">

    <h1>Générateur de numéro de sécurité sociale</h1>

    <label for="date_naissance">Date de naissance</label>
    <input type="date" name="date_naissance" id="date_naissance" required>
    <div id="date_naissance_error" class="error"></div>

    <input type="button" value="Générer" id="generer">

  </form>

  <script>
    function genererNumeroSecuriteSociale() {
      // Récupère les données du formulaire
      const dateNaissance = document.querySelector("#date_naissance").value;

      // Vérifie que le champ "Date de naissance" est rempli
      if (dateNaissance === "") {
        document.querySelector("#date_naissance_error").textContent = "Veuillez entrer une date de naissance.";
        return;
      } else {
        document.querySelector("#date_naissance_error").textContent = "";
      }

      // Génère le numéro de sécurité sociale
      const anneeNaissance = dateNaissance.substr(2, 2); // Prend les deux derniers chiffres de l'année
      const moisNaissance = dateNaissance.substr(5, 2);
      const jourNaissance = dateNaissance.substr(8, 2);
      const departement = 974;
      const numeroAleatoire = Math.floor(Math.random() * 99999);
      const numeroSecuriteSociale = `9${anneeNaissance}${moisNaissance}${jourNaissance}${departement}${numeroAleatoire.toString().padStart(4, '0')}`.substr(0, 15);

      // Affiche le numéro de sécurité sociale
      document.querySelector("#numero_securite_sociale").textContent = `Numéro de sécurité sociale généré : ${numeroSecuriteSociale}`;
    }

    document.querySelector("#generer").addEventListener("click", genererNumeroSecuriteSociale);

    // Vérifie que le champ "Date de naissance" est rempli
    document.querySelector("#date_naissance").addEventListener("change", function () {
      if (this.value === "") {
        this.classList.add("is-invalid");
      } else {
        this.classList.remove("is-invalid");
      }
    });

  </script>

  <p id="numero_securite_sociale"></p>
</body>
</html>
