
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

    <form onsubmit="sendWhatsApp(); return false;">

      <label>Adresse de pick-up</label>
      <input type="text" id="pickup" required />

      <label>Date et heure de pick-up</label>
      <input type="datetime-local" id="datetime" required />

      <label>Adresse de dépose</label>
      <input type="text" id="dropoff" required />

      <label>Nombre de passagers</label>
      <input type="number" id="passengers" required />

      <label>Nom(s)</label>
      <input type="text" id="names" required />

      <label>Numéro de téléphone</label>
      <input type="tel" id="phone" required />

      <label>Informations supplémentaires</label>
      <textarea id="infos" placeholder="Vol, train, terminal, demandes particulières..."></textarea>

      <button type="submit">ENVOYER LA DEMANDE VIA WHATSAPP</button>
    </form>

    <div class="footer">
      © QP TRANSPORT – VTC Premium
    </div>

  </div>

  <script>
    function sendWhatsApp() {
      const pickup = document.getElementById('pickup').value;
      const datetime = document.getElementById('datetime').value;
      const dropoff = document.getElementById('dropoff').value;
      const passengers = document.getElementById('passengers').value;
      const names = document.getElementById('names').value;
      const phone = document.getElementById('phone').value;
      const infos = document.getElementById('infos').value;

      const message = `Bonjour QP TRANSPORT,%0A%0AJe souhaite réserver un VTC.%0A%0A📍 Pick-up : ${pickup}%0A🕒 Date & heure : ${datetime}%0A📍 Dépose : ${dropoff}%0A👥 Passagers : ${passengers}%0A👤 Nom(s) : ${names}%0A📞 Téléphone : ${phone}%0A✈️ Infos : ${infos}`;

      const url = `https://wa.me/33635215052?text=${message}`;
      window.open(url, '_blank');
    }
  </script>

</body>
</html>
