<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Bienvenidos con carro</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      height: 100%;
      width: 100%;
      overflow: hidden;
      font-family: Arial, sans-serif;
    }

    #pantalla1, #pantalla2 {
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
    }

    #pantalla1 {
      background: black;
      color: white;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      font-size: 3em;
      z-index: 1;
    }

    #textoBienvenida {
      z-index: 10;
    }

    #carro {
      position: absolute;
      bottom: 20px;
      left: -150px;
      width: 150px;
      height: 80px;
      background: red;
      border-radius: 15px;
      box-shadow: 0 0 10px 2px #c00 inset;
      animation: moverCarro 6s forwards;
      z-index: 20;
    }

    #carro::before {
      content: "";
      position: absolute;
      top: 15px;
      left: 10px;
      width: 50px;
      height: 50px;
      background: black;
      border-radius: 50%;
      box-shadow: 80px 0 0 black;
    }

    @keyframes moverCarro {
      0% { left: -150px; }
      50% { left: 40%; }
      100% { left: 110%; }
    }

    @keyframes salidaTexto {
      0% { opacity: 1; transform: translateX(0); }
      100% { opacity: 0; transform: translateX(120%); }
    }

    .salir {
      animation: salidaTexto 6s forwards;
    }

    #pantalla2 {
      display: none;
      background: #111;
      color: white;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 2;
    }

    #youtube {
      width: 90%;
      height: 60%;
      margin-bottom: 20px;
      border-radius: 8px;
      box-shadow: 0 0 20px #000;
    }

    #boton {
      padding: 15px 30px;
      font-size: 1.5em;
      background-color: #007bff;
      border: none;
      border-radius: 8px;
      color: white;
      cursor: pointer;
      text-decoration: none;
    }

    #boton:hover {
      background-color: #0056b3;
    }
  </style>
</head>
<body>

  <!-- Pantalla 1 -->
  <div id="pantalla1">
    <div id="textoBienvenida">¡BIENVENIDOS!</div>
    <div id="carro"></div>
  </div>

  <!-- Pantalla 2 -->
  <div id="pantalla2" style="display: flex;">
    <iframe
      id="youtube"
      src="https://www.youtube.com/embed/lbesWnIA198?autoplay=1&mute=0&controls=0&modestbranding=1&rel=0&playsinline=1"
      frameborder="0"
      allow="autoplay; encrypted-media"
      allowfullscreen
    ></iframe>
    <a id="boton" href="https://docs.google.com/forms/d/e/1FAIpQLSdYUTYDEO3hyEH_8IgpCBmzujNeE-ARsPKVYFKtfiZXkFSEkQ/viewform?usp=dialog" target="_blank">Ir al formulario</a>
  </div>

  <script>
    const texto = document.getElementById('textoBienvenida');
    const carro = document.getElementById('carro');
    const pantalla1 = document.getElementById('pantalla1');
    const pantalla2 = document.getElementById('pantalla2');

    carro.addEventListener('animationstart', () => {
      texto.classList.add('salir');
    });

    carro.addEventListener('animationend', () => {
      pantalla1.style.display = 'none';
      pantalla2.style.display = 'flex';
    });
  </script>

</body>
</html>
