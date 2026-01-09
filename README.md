<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Réservation VTC – QP TRANSPORT</title>
  <style>
    body {
      font-family: 'Segoe UI', Arial, sans-serif;
      background: radial-gradient(circle at top, #1a1a1a, #000000);
      margin: 0;
      padding: 0;
      color: #e5e5e5;
    }
    .container {
      max-width: 600px;
      margin: 40px auto;
      background: #0f0f0f;
      padding: 30px;
      border-radius: 14px;
      box-shadow: 0 0 30px rgba(0,0,0,0.7);
      border: 1px solid rgba(212,175,55,0.25);
    }
    .logo {
      display: flex;
      justify-content: center;
      margin-bottom: 20px;
    }
    .logo img {
      max-width: 220px;
    }
    h1 {
      text-align: center;
      color: #d4af37;
      letter-spacing: 2px;
      margin-bottom: 10px;
    }
    p {
      text-align: center;
      color: #cfcfcf;
      font-size: 14px;
      margin-bottom: 25px;
    }
    label {
      display: block;
      margin-top: 18px;
      font-weight: 600;
      color: #d4af37;
      font-size: 13px;
    }
    input, textarea {
      width: 100%;
      padding: 11px;
      margin-top: 6px;
      border-radius: 8px;
      border: 1px solid #333;
      background: #1b1b1b;
      color: #fff;
      font-size: 14px;
    }
    input:focus, textarea:focus {
      outline: none;
      border-color: #d4af37;
    }
    textarea {
      resize: vertical;
    }
    button {
      margin-top: 30px;
      width: 100%;
      padding: 14px;
      background: linear-gradient(135deg, #d4af37, #b8962e);
      color: #000;
      border: none;
      border-radius: 30px;
      font-size: 15px;
      font-weight: 600;
      cursor: pointer;
      letter-spacing: 1px;
    }
    button:hover {
      opacity: 0.9;
    }
    .footer {
      margin-top: 25px;
      text-align: center;
      font-size: 12px;
      color: #777;
    }
  </style>
</head>
<body>

  <div class="container">

    <div class="logo">
      <img src="logo-qp-transport.png" alt="QP Transport" />
    </div>

    <h1>RÉSERVATION VTC</h1>
    <p>Service de transport privé haut de gamme</p>

    <form id="booking-form">

      <label>Adresse de pick-up</label>
      <input type="text" id="pickup" name="pickup" required />

      <label>Date et heure de pick-up</label>
      <input type="datetime-local" id="datetime" name="datetime" required />

      <label>Adresse de dépose</label>
      <input type="text" id="dropoff" name="dropoff" required />

      <label>Nombre de passagers</label>
      <input type="number" id="passengers" name="passengers" required />

      <label>Nom(s)</label>
      <input type="text" id="names" name="names" required />

      <label>Numéro de téléphone</label>
      <input type="tel" id="phone" name="phone" required />

      <label>Informations supplémentaires</label>
      <textarea id="infos" name="infos" placeholder="Vol, train, terminal, demandes particulières..."></textarea>

      <button type="submit">ENVOYER LA DEMANDE</button>
    </form>

    <div class="footer">
      © QP TRANSPORT – VTC Premium
    </div>

  </div>

  <!-- EmailJS Script -->
  <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
  <script>
    emailjs.init("YOUR_PUBLIC_KEY"); // Remplace par ta Public Key EmailJS

    document.getElementById('booking-form').addEventListener('submit', function(e) {
      e.preventDefault();

      const formData = {
        pickup: document.getElementById('pickup').value,
        datetime: document.getElementById('datetime').value,
        dropoff: document.getElementById('dropoff').value,
        passengers: document.getElementById('passengers').value,
        names: document.getElementById('names').value,
        phone: document.getElementById('phone').value,
        infos: document.getElementById('infos').value
      };

      emailjs.send("YOUR_SERVICE_ID", "YOUR_TEMPLATE_ID", formData)
        .then(function() {
          alert("Votre demande a été envoyée ! Merci.");
          document.getElementById('booking-form').reset();
        }, function(error) {
          alert("Erreur lors de l'envoi : " + JSON.stringify(error));
        });
    });
  </script>

</body>
</html>
