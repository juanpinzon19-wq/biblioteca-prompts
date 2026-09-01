# biblioteca-prompts

1. Navbar responsive

Variables:

{BRAND_COLOR}: Color principal de la marca (ej. código HEX o clase de Tailwind).
{COMPANY_NAME}: Nombre de la empresa o texto del logo.
{NAV_LINKS}: Lista de enlaces separados por comas.

Prompt:
Actúa como un desarrollador frontend experto. Genera un menú de navegación responsivo usando HTML y CSS (Flexbox). El fondo debe usar el color {BRAND_COLOR}. A la izquierda, muestra el logo con el texto "{COMPANY_NAME}". A la derecha, incluye los enlaces: {NAV_LINKS}. En dispositivos móviles (menor a 768px), los enlaces deben ocultarse y debe aparecer un botón de menú hamburguesa.

Ejemplo de uso:
Actúa como un desarrollador frontend experto. Genera un menú de navegación responsivo usando HTML y CSS (Flexbox). El fondo debe usar el color #1A56DB. A la izquierda, muestra el logo con el texto "TechSolutions". A la derecha, incluye los enlaces: Inicio, Servicios, Sobre Nosotros, Contacto. En dispositivos móviles (menor a 768px), los enlaces deben ocultarse y debe aparecer un botón de menú hamburguesa.

Código generado esperado:

HTML
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TechSolutions - Navegación</title>
    <link rel="stylesheet" href="style.css">
    <!-- Iconos opcionales para el menú hamburguesa -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
</head>
<body>

    <nav class="navbar">
        <div class="container">
            <div class="logo">
                <a href="#">TechSolutions</a>
            </div>

            <!-- Botón Hamburguesa -->
            <button class="menu-toggle" id="mobile-menu" aria-label="Abrir menú">
                <span class="bar"></span>
                <span class="bar"></span>
                <span class="bar"></span>
            </button>

            <!-- Enlaces de navegación -->
            <ul class="nav-links">
                <li><a href="#inicio">Inicio</a></li>
                <li><a href="#servicios">Servicios</a></li>
                <li><a href="#sobre-nosotros">Sobre Nosotros</a></li>
                <li><a href="#contacto" class="btn-contacto">Contacto</a></li>
            </ul>
        </div>
    </nav>

    <script src="script.js"></script>
</body>
</html>

CSS
/* Reset básico */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

:root {
    --primary-color: #1A56DB;
    --white: #ffffff;
    --transition: all 0.3s ease;
}

body {
    background-color: #f4f4f4;
}

/* Navbar Principal */
.navbar {
    background-color: var(--primary-color);
    height: 80px;
    display: flex;
    align-items: center;
    position: sticky;
    top: 0;
    z-index: 1000;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.container {
    width: 90%;
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo a {
    color: var(--white);
    font-size: 1.5rem;
    font-weight: bold;
    text-decoration: none;
    letter-spacing: 1px;
}

/* Enlaces Desktop */
.nav-links {
    display: flex;
    list-style: none;
    align-items: center;
}

.nav-links li {
    margin-left: 30px;
}

.nav-links a {
    color: var(--white);
    text-decoration: none;
    font-size: 1rem;
    font-weight: 500;
    transition: var(--transition);
    opacity: 0.9;
}

.nav-links a:hover {
    opacity: 1;
    color: #e2e8f0;
}

/* Botón Hamburguesa (Oculto en Desktop) */
.menu-toggle {
    display: none;
    flex-direction: column;
    cursor: pointer;
    background: transparent;
    border: none;
}

.menu-toggle .bar {
    width: 25px;
    height: 3px;
    background-color: var(--white);
    margin: 4px 0;
    transition: var(--transition);
}

/* --- RESPONSIVE (Móvil < 768px) --- */
@media screen and (max-width: 768px) {
    .menu-toggle {
        display: flex;
    }

    .nav-links {
        position: absolute;
        top: 80px;
        left: -100%; /* Oculto fuera de pantalla */
        flex-direction: column;
        background-color: var(--primary-color);
        width: 100%;
        text-align: center;
        transition: var(--transition);
        box-shadow: 0 10px 10px rgba(0,0,0,0.1);
        padding: 20px 0;
    }

    .nav-links.active {
        left: 0; /* Desliza hacia adentro */
    }

    .nav-links li {
        margin: 15px 0;
    }

    /* Animación del menú hamburguesa a "X" */
    .menu-toggle.is-active .bar:nth-child(2) { opacity: 0; }
    .menu-toggle.is-active .bar:nth-child(1) { transform: translateY(11px) rotate(45deg); }
    .menu-toggle.is-active .bar:nth-child(3) { transform: translateY(-11px) rotate(-45deg); }
}

JavaScript
const menu = document.querySelector('#mobile-menu');
const menuLinks = document.querySelector('.nav-links');

menu.addEventListener('click', () => {
    menu.classList.toggle('is-active');
    menuLinks.classList.toggle('active');
});

// Cerrar el menú al hacer clic en un enlace (opcional, recomendado para UX)
document.querySelectorAll('.nav-links a').forEach(n => n.addEventListener('click', () => {
    menu.classList.remove('is-active');
    menuLinks.classList.remove('active');
}));


2. Hero section

Variables:

{MAIN_HEADLINE}: Título principal h1.
{SUBTITLE}: Párrafo descriptivo debajo del título.
{CTA_TEXT}: Texto del botón principal.
{BG_IMAGE}: URL de la imagen de fondo.

Prompt:
Genera el código HTML y CSS para una sección Hero moderna. Debe tener una imagen de fondo ({BG_IMAGE}) con un overlay oscuro del 50% para mejorar la legibilidad. En el centro, coloca el titular <h1> "{MAIN_HEADLINE}", seguido de un párrafo <p> "{SUBTITLE}". Debajo, incluye un botón de llamada a la acción prominente que diga "{CTA_TEXT}".

Ejemplo de uso:
Genera el código HTML y CSS para una sección Hero moderna. Debe tener una imagen de fondo ([https://ejemplo.com/hero.jpg](https://www.google.com/url?sa=E&source=gmail&q=https://ejemplo.com/hero.jpg)) con un overlay oscuro del 50% para mejorar la legibilidad. En el centro, coloca el titular <h1> "Transforma tu negocio digital", seguido de un párrafo <p> "Soluciones de software a medida para escalar tus ventas". Debajo, incluye un botón de llamada a la acción prominente que diga "Comenzar Ahora".

Código generado esperado:

HTML
<section class="hero">
    <div class="hero-container">
        <div class="hero-content">
            <h1>Transforma tu negocio digital</h1>
            <p>Soluciones de software a medida para escalar tus ventas</p>
            <a href="#contacto" class="btn-cta">Comenzar Ahora</a>
        </div>
    </div>
</section>

CSS
/* --- SECCIÓN HERO --- */
.hero {
    /* Imagen de fondo con overlay del 50% (negro semi-transparente) */
    background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), 
                url('https://ejemplo.com/hero.jpg');
    
    /* Configuración de la imagen */
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    background-attachment: fixed; /* Efecto Parallax sutil */
    
    /* Dimensiones y Centrado */
    height: 90vh; /* Ocupa el 90% de la altura de la pantalla */
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    color: var(--white);
    padding: 0 20px;
}

.hero-content {
    max-width: 800px;
    /* Animación de entrada */
    animation: fadeInUp 1s ease-out;
}

.hero-content h1 {
    font-size: 3.5rem;
    font-weight: 800;
    margin-bottom: 1.5rem;
    line-height: 1.2;
    text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.3);
}

.hero-content p {
    font-size: 1.25rem;
    margin-bottom: 2.5rem;
    opacity: 0.9;
    font-weight: 300;
}

/* Botón de Llamada a la Acción (CTA) */
.btn-cta {
    display: inline-block;
    background-color: var(--primary-color); /* El azul #1A56DB */
    color: var(--white);
    padding: 18px 35px;
    font-size: 1.1rem;
    font-weight: 600;
    text-decoration: none;
    border-radius: 50px;
    transition: all 0.3s ease;
    box-shadow: 0 4px 15px rgba(26, 86, 219, 0.3);
}

.btn-cta:hover {
    background-color: #1649b8;
    transform: translateY(-3px);
    box-shadow: 0 6px 20px rgba(26, 86, 219, 0.4);
}

.btn-cta:active {
    transform: translateY(-1px);
}

/* Keyframes para la animación de entrada */
@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* --- Ajustes Responsivos --- */
@media screen and (max-width: 768px) {
    .hero {
        height: 80vh;
        background-attachment: scroll; /* Desactivar parallax en móviles para rendimiento */
    }

    .hero-content h1 {
        font-size: 2.2rem;
    }

    .hero-content p {
        font-size: 1.1rem;
    }

    .btn-cta {
        padding: 15px 30px;
        width: 100%; /* El botón ocupa el ancho total en móviles pequeños si es necesario */
        max-width: 280px;
    }
}



3. Card component

Variables:

{IMAGE_URL}: URL de la imagen de la tarjeta.
{CARD_TITLE}: Título de la tarjeta.
{CARD_DESC}: Descripción breve.
{BADGE_TEXT}: Texto de la etiqueta/badge superior.

Prompt:
Crea un componente de tarjeta (Card) usando HTML y Tailwind CSS. La tarjeta debe tener bordes redondeados y una sombra suave. En la parte superior, muestra la imagen {IMAGE_URL}. Sobre la imagen, en la esquina superior derecha, incluye un badge pequeño que diga "{BADGE_TEXT}". Debajo de la imagen, coloca el título "{CARD_TITLE}" en negrita y la descripción "{CARD_DESC}".

Ejemplo de uso:
Crea un componente de tarjeta (Card) usando HTML y Tailwind CSS. La tarjeta debe tener bordes redondeados y una sombra suave. En la parte superior, muestra la imagen [https://via.placeholder.com/300](https://www.google.com/url?sa=E&source=gmail&q=https://via.placeholder.com/300). Sobre la imagen, en la esquina superior derecha, incluye un badge pequeño que diga "Nuevo". Debajo de la imagen, coloca el título "Zapatillas Runner X" en negrita y la descripción "Zapatillas ultraligeras para correr en asfalto.".

Código generado esperado:

HTML
<!-- CDN de Tailwind para pruebas rápidas -->
<script src="https://cdn.tailwindcss.com"></script>

<div class="flex justify-center items-center min-h-screen bg-gray-100 p-6">
  
  <!-- Tarjeta (Card) -->
  <div class="max-w-xs bg-white rounded-2xl shadow-md overflow-hidden hover:shadow-xl transition-shadow duration-300">
    
    <!-- Contenedor de Imagen y Badge -->
    <div class="relative">
      <img 
        src="https://via.placeholder.com/300" 
        alt="Zapatillas Runner X" 
        class="w-full h-56 object-cover"
      />
      
      <!-- Badge "Nuevo" -->
      <span class="absolute top-3 right-3 bg-blue-600 text-white text-[10px] font-bold px-2.5 py-1 rounded-full uppercase tracking-wider shadow-sm">
        Nuevo
      </span>
    </div>

    <!-- Contenido de la tarjeta -->
    <div class="p-5">
      <h3 class="text-gray-900 text-xl font-bold mb-2">
        Zapatillas Runner X
      </h3>
      <p class="text-gray-600 text-sm leading-relaxed">
        Zapatillas ultraligeras para correr en asfalto.
      </p>
      
      <!-- Opcional: Un botón para completar el diseño -->
      <button class="mt-4 w-full bg-gray-900 text-white text-sm font-semibold py-2 rounded-lg hover:bg-gray-800 transition-colors">
        Ver detalles
      </button>
    </div>
  </div>

</div>




4. Formulario de contacto

Variables:

{FORM_TITLE}: Título del formulario.
{FIELDS}: Lista de campos a incluir (ej. Nombre, Email, Teléfono, Mensaje).
{BUTTON_COLOR}: Color del botón de envío.

Prompt:
Escribe el HTML para un formulario de contacto accesible. El título debe ser "{FORM_TITLE}". Incluye los siguientes campos con sus respectivas etiquetas <label> e inputs/textareas adecuados: {FIELDS}. Todos los campos deben ser requeridos. El botón de envío debe tener el color de fondo {BUTTON_COLOR}.

Ejemplo de uso:
Escribe el HTML para un formulario de contacto accesible. El título debe ser "Hablemos de tu proyecto". Incluye los siguientes campos con sus respectivas etiquetas <label> e inputs/textareas adecuados: Nombre completo, Correo electrónico, Empresa, Mensaje. Todos los campos deben ser requeridos. El botón de envío debe tener el color de fondo #4CAF50.

Código generado esperado:

HTML
<section class="contact-form-container">
    <div class="form-card">
        <h2>Hablemos de tu proyecto</h2>
        
        <form action="#" method="POST" id="contact-form">
            <!-- Nombre Completo -->
            <div class="form-group">
                <label for="full-name">Nombre completo</label>
                <input 
                    type="text" 
                    id="full-name" 
                    name="full-name" 
                    placeholder="Ej. Juan Pérez" 
                    required 
                    aria-required="true"
                >
            </div>

            <!-- Correo Electrónico -->
            <div class="form-group">
                <label for="email">Correo electrónico</label>
                <input 
                    type="email" 
                    id="email" 
                    name="email" 
                    placeholder="juan@ejemplo.com" 
                    required 
                    aria-required="true"
                >
            </div>

            <!-- Empresa -->
            <div class="form-group">
                <label for="company">Empresa</label>
                <input 
                    type="text" 
                    id="company" 
                    name="company" 
                    placeholder="Nombre de tu empresa" 
                    required 
                    aria-required="true"
                >
            </div>

            <!-- Mensaje -->
            <div class="form-group">
                <label for="message">Mensaje</label>
                <textarea 
                    id="message" 
                    name="message" 
                    rows="5" 
                    placeholder="Cuéntanos sobre tu idea..." 
                    required 
                    aria-required="true"
                ></textarea>
            </div>

            <!-- Botón de Envío -->
            <button type="submit" class="btn-submit">Enviar Mensaje</button>
        </form>
    </div>
</section>

CSS
:root {
    --primary-success: #4CAF50;
    --text-dark: #333;
    --text-light: #666;
    --border-color: #ddd;
    --focus-ring: #2196F3;
}

.contact-form-container {
    display: flex;
    justify-content: center;
    padding: 40px 20px;
    font-family: 'Inter', system-ui, -apple-system, sans-serif;
}

.form-card {
    background: #ffffff;
    padding: 30px;
    border-radius: 12px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
    width: 100%;
    max-width: 500px;
}

h2 {
    color: var(--text-dark);
    margin-bottom: 25px;
    font-size: 1.8rem;
    text-align: center;
}

.form-group {
    margin-bottom: 20px;
    display: flex;
    flex-direction: column;
}

/* Estilos de Etiquetas (Labels) */
label {
    font-weight: 600;
    margin-bottom: 8px;
    color: var(--text-dark);
    font-size: 0.95rem;
}

/* Estilos de Inputs y Textarea */
input, textarea {
    padding: 12px 16px;
    border: 1px solid var(--border-color);
    border-radius: 6px;
    font-size: 1rem;
    transition: border-color 0.2s, box-shadow 0.2s;
    outline: none;
}

/* Estado Focus: Crucial para la navegación por teclado */
input:focus, textarea:focus {
    border-color: var(--focus-ring);
    box-shadow: 0 0 0 3px rgba(33, 150, 243, 0.2);
}

/* Estilo del Botón solicitado */
.btn-submit {
    width: 100%;
    background-color: var(--primary-success); /* #4CAF50 */
    color: white;
    padding: 14px;
    border: none;
    border-radius: 6px;
    font-size: 1.1rem;
    font-weight: bold;
    cursor: pointer;
    transition: background-color 0.3s ease;
    margin-top: 10px;
}

.btn-submit:hover {
    background-color: #43a047; /* Un tono más oscuro al pasar el mouse */
}

.btn-submit:focus {
    outline: 2px solid white;
    outline-offset: -4px;
    box-shadow: 0 0 0 3px rgba(76, 175, 80, 0.4);
}

/* Mejoras para dispositivos móviles */
@media (max-width: 480px) {
    .form-card {
        padding: 20px;
    }
    
    h2 {
        font-size: 1.5rem;
    }
}



5. Footer

Variables:

{COMPANY_NAME}: Nombre de tu empresa.
{COLUMNS}: Nombres de las columnas de enlaces.
{SOCIAL_NETWORKS}: Redes sociales a incluir.

Prompt:
Diseña un Footer oscuro usando HTML y CSS Grid. Debe tener un diseño de columnas basado en: {COLUMNS}. En la primera columna, incluye el nombre "{COMPANY_NAME}" y una breve descripción. En la última columna, añade íconos o enlaces para las redes sociales: {SOCIAL_NETWORKS}. Al fondo, incluye una línea separadora y el texto de copyright dinámico con el año actual.

Ejemplo de uso:
Diseña un Footer oscuro usando HTML y CSS Grid. Debe tener un diseño de columnas basado en: Producto, Recursos, Legal. En la primera columna, incluye el nombre "SaaSify" y una breve descripción. En la última columna, añade íconos o enlaces para las redes sociales: Twitter, LinkedIn, GitHub. Al fondo, incluye una línea separadora y el texto de copyright dinámico con el año actual.

Código generado esperado:

HTML
<footer class="main-footer">
    <div class="footer-container">
        <!-- Columna 1: Branding -->
        <div class="footer-brand">
            <h2 class="footer-logo">SaaSify</h2>
            <p>La plataforma integral para gestionar tu flujo de trabajo con inteligencia artificial y análisis en tiempo real.</p>
        </div>

        <!-- Columna 2: Producto -->
        <div class="footer-links">
            <h3>Producto</h3>
            <ul>
                <li><a href="#">Funcionalidades</a></li>
                <li><a href="#">Precios</a></li>
                <li><a href="#">Integraciones</a></li>
                <li><a href="#">Enterprise</a></li>
            </ul>
        </div>

        <!-- Columna 3: Recursos -->
        <div class="footer-links">
            <h3>Recursos</h3>
            <ul>
                <li><a href="#">Documentación</a></li>
                <li><a href="#">Guías</a></li>
                <li><a href="#">Soporte</a></li>
                <li><a href="#">API</a></li>
            </ul>
        </div>

        <!-- Columna 4: Legal y Redes -->
        <div class="footer-links">
            <h3>Legal</h3>
            <ul>
                <li><a href="#">Privacidad</a></li>
                <li><a href="#">Términos</a></li>
                <li><a href="#">Cookies</a></li>
            </ul>
            <div class="social-links">
                <a href="#" aria-label="Twitter"><i class="fab fa-twitter"></i></a>
                <a href="#" aria-label="LinkedIn"><i class="fab fa-linkedin"></i></a>
                <a href="#" aria-label="GitHub"><i class="fab fa-github"></i></a>
            </div>
        </div>
    </div>

    <!-- Separador y Copyright -->
    <div class="footer-bottom">
        <hr class="footer-divider">
        <p>&copy; <span id="current-year"></span> SaaSify. Todos los derechos reservados.</p>
    </div>
</footer>

<!-- Font Awesome para los iconos de redes sociales -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/js/all.min.js"></script>

CSS
/* Variables de color para tema oscuro */
:root {
    --footer-bg: #0f172a; /* Azul muy oscuro */
    --footer-text: #94a3b8; /* Gris azulado suave */
    --footer-white: #f8fafc;
    --accent-color: #38bdf8; /* Azul claro para hovers */
}

.main-footer {
    background-color: var(--footer-bg);
    color: var(--footer-text);
    padding: 60px 0 30px 0;
    font-family: 'Inter', sans-serif;
}

.footer-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
    
    /* Configuración de CSS Grid */
    display: grid;
    grid-template-columns: 1fr; /* 1 columna en móvil */
    gap: 40px;
}

/* Cambio a 4 columnas en Desktop */
@media (min-width: 768px) {
    .footer-container {
        grid-template-columns: 2fr 1fr 1fr 1fr;
    }
}

.footer-logo {
    color: var(--footer-white);
    font-size: 1.5rem;
    font-weight: 700;
    margin-bottom: 1rem;
}

.footer-brand p {
    line-height: 1.6;
    max-width: 300px;
}

.footer-links h3 {
    color: var(--footer-white);
    font-size: 1rem;
    font-weight: 600;
    margin-bottom: 1.2rem;
    text-transform: uppercase;
    letter-spacing: 0.05em;
}

.footer-links ul {
    list-style: none;
    padding: 0;
}

.footer-links li {
    margin-bottom: 0.8rem;
}

.footer-links a {
    color: var(--footer-text);
    text-decoration: none;
    transition: color 0.3s ease;
}

.footer-links a:hover {
    color: var(--accent-color);
}

/* Iconos de Redes Sociales */
.social-links {
    margin-top: 1.5rem;
    display: flex;
    gap: 15px;
}

.social-links a {
    font-size: 1.2rem;
    color: var(--footer-text);
}

.social-links a:hover {
    color: var(--footer-white);
    transform: translateY(-3px);
}

/* Parte inferior */
.footer-bottom {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
    text-align: center;
    margin-top: 50px;
}

.footer-divider {
    border: 0;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    margin-bottom: 25px;
}

.footer-bottom p {
    font-size: 0.85rem;
}

JavaScript
document.addEventListener('DOMContentLoaded', () => {
    const yearSpan = document.getElementById('current-year');
    yearSpan.textContent = new Date().getFullYear();
});




6. Modal/Dialog

Variables:

{MODAL_TITLE}: Título del cuadro de diálogo.
{MODAL_BODY}: Texto o contenido principal del modal.
{CONFIRM_TEXT}: Texto del botón de confirmación.
{CANCEL_TEXT}: Texto del botón de cancelación.

Prompt:
Proporciona el HTML y Vanilla JavaScript para un componente Modal accesible. El título del modal es "{MODAL_TITLE}" y el cuerpo contiene el texto: "{MODAL_BODY}". Debe tener dos botones en la parte inferior: uno para cancelar que diga "{CANCEL_TEXT}" y uno principal que diga "{CONFIRM_TEXT}". Incluye el JS para abrirlo mediante un botón externo y cerrarlo al hacer clic en la X, en el botón de cancelar, o fuera del modal.

Ejemplo de uso:
Proporciona el HTML y Vanilla JavaScript para un componente Modal accesible. El título del modal es "Eliminar cuenta" y el cuerpo contiene el texto: "¿Estás seguro de que deseas eliminar tu cuenta permanentemente? Esta acción no se puede deshacer.". Debe tener dos botones en la parte inferior: uno para cancelar que diga "Cancelar" y uno principal que diga "Sí, eliminar". Incluye el JS para abrirlo mediante un botón externo y cerrarlo al hacer clic en la X, en el botón de cancelar, o fuera del modal.

Código generado esperado:

HTML
<!-- Botón disparador -->
<button id="openModalBtn" class="btn-trigger">Eliminar mi cuenta</button>

<!-- Estructura del Modal -->
<div id="modalOverlay" class="modal-overlay" aria-hidden="true">
    <div class="modal-container" 
         role="dialog" 
         aria-modal="true" 
         aria-labelledby="modalTitle" 
         aria-describedby="modalDescription">
        
        <!-- Botón cerrar (X) -->
        <button class="close-x" id="closeX" aria-label="Cerrar modal">&times;</button>

        <div class="modal-content">
            <h2 id="modalTitle">Eliminar cuenta</h2>
            <p id="modalDescription">
                ¿Estás seguro de que deseas eliminar tu cuenta permanentemente? 
                Esta acción no se puede deshacer.
            </p>
        </div>

        <div class="modal-footer">
            <button class="btn-secondary" id="cancelBtn">Cancelar</button>
            <button class="btn-danger" id="confirmBtn">Sí, eliminar</button>
        </div>
    </div>
</div>

CSS
:root {
    --overlay-bg: rgba(0, 0, 0, 0.6);
    --modal-bg: #ffffff;
    --danger: #dc3545;
    --secondary: #6c757d;
}

/* Overlay (Fondo oscuro) */
.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: var(--overlay-bg);
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    visibility: hidden;
    transition: all 0.3s ease;
    z-index: 2000;
}

/* Estado activo del modal */
.modal-overlay.is-visible {
    opacity: 1;
    visibility: visible;
}

/* Contenedor del Modal */
.modal-container {
    background: var(--modal-bg);
    width: 90%;
    max-width: 450px;
    border-radius: 12px;
    padding: 24px;
    position: relative;
    transform: scale(0.8);
    transition: transform 0.3s ease;
    box-shadow: 0 10px 25px rgba(0,0,0,0.2);
}

.modal-overlay.is-visible .modal-container {
    transform: scale(1);
}

/* Botón cerrar X */
.close-x {
    position: absolute;
    top: 15px;
    right: 15px;
    background: none;
    border: none;
    font-size: 24px;
    cursor: pointer;
    color: #999;
}

.close-x:hover { color: #333; }

/* Contenido */
#modalTitle { margin-top: 0; color: #1a202c; }
#modalDescription { color: #4a5568; line-height: 1.5; margin: 15px 0 25px; }

/* Botones del Footer */
.modal-footer {
    display: flex;
    justify-content: flex-end;
    gap: 12px;
}

button {
    padding: 10px 20px;
    border-radius: 6px;
    font-weight: 600;
    cursor: pointer;
    border: none;
    transition: opacity 0.2s;
}

.btn-secondary { background: #e2e8f0; color: #4a5568; }
.btn-danger { background: var(--danger); color: white; }
button:hover { opacity: 0.9; }

/* Estilo para el disparador */
.btn-trigger { background: var(--danger); color: white; padding: 12px 24px; font-size: 1rem; }

JavaScript
const openModalBtn = document.getElementById('openModalBtn');
const modalOverlay = document.getElementById('modalOverlay');
const closeX = document.getElementById('closeX');
const cancelBtn = document.getElementById('cancelBtn');

// Guardar qué elemento tenía el foco antes de abrir el modal
let lastFocusedElement;

const openModal = () => {
    lastFocusedElement = document.activeElement; // Guardar el botón que abrió
    modalOverlay.classList.add('is-visible');
    modalOverlay.setAttribute('aria-hidden', 'false');
    
    // Bloquear scroll del cuerpo
    document.body.style.overflow = 'hidden';

    // Poner el foco en el primer botón del modal (Cancelar para evitar borrados accidentales)
    setTimeout(() => cancelBtn.focus(), 100);
};

const closeModal = () => {
    modalOverlay.classList.remove('is-visible');
    modalOverlay.setAttribute('aria-hidden', 'true');
    
    // Restaurar scroll
    document.body.style.overflow = '';

    // Devolver el foco al botón que abrió el modal (Vital para accesibilidad)
    if (lastFocusedElement) lastFocusedElement.focus();
};

// Eventos de apertura y cierre
openModalBtn.addEventListener('click', openModal);
closeX.addEventListener('click', closeModal);
cancelBtn.addEventListener('click', closeModal);

// Cerrar al hacer clic fuera del contenedor blanco (en el overlay)
modalOverlay.addEventListener('click', (e) => {
    if (e.target === modalOverlay) closeModal();
});

// Cerrar con la tecla Escape
document.addEventListener('keydown', (e) => {
    if (e.key === 'Escape' && modalOverlay.classList.contains('is-visible')) {
        closeModal();
    }
});




7. Accordion/FAQ

Variables:

{FAQ_LIST}: Lista de Preguntas y Respuestas.
{TRANSITION_SPEED}: Velocidad de la animación (ej. 0.3s).
{ICON_OPEN}: Símbolo cuando está abierto.
{ICON_CLOSED}: Símbolo cuando está cerrado.

Prompt:
Crea un componente de Acordeón interactivo para una sección de Preguntas Frecuentes usando la etiqueta <details> y <summary> nativas de HTML. Inserta las siguientes preguntas y respuestas: {FAQ_LIST}. Usa CSS para eliminar el marcador por defecto y reemplazarlo por "{ICON_CLOSED}" cuando esté cerrado y "{ICON_OPEN}" cuando esté abierto. Añade una transición de {TRANSITION_SPEED} al expandir el contenido.

Ejemplo de uso:
Crea un componente de Acordeón interactivo para una sección de Preguntas Frecuentes usando la etiqueta <details> y <summary> nativas de HTML. Inserta las siguientes preguntas y respuestas: 1. ¿Cuál es el costo? - Es gratis, 2. ¿Ofrecen soporte? - Sí, 24/7. Usa CSS para eliminar el marcador por defecto y reemplazarlo por "+" cuando esté cerrado y "-" cuando esté abierto. Añade una transición de 0.3s al expandir el contenido.

Código generado esperado:

HTML
<section class="faq-section">
    <h2>Preguntas Frecuentes</h2>

    <details class="faq-item">
        <summary>¿Cuál es el costo?</summary>
        <div class="faq-content">
            <p>Es gratis.</p>
        </div>
    </details>

    <details class="faq-item">
        <summary>¿Ofrecen soporte?</summary>
        <div class="faq-content">
            <p>Sí, ofrecemos soporte dedicado 24/7 para todos nuestros usuarios.</p>
        </div>
    </details>
</section>

CSS
:root {
    --primary-blue: #1A56DB;
    --border-color: #e5e7eb;
    --text-color: #374151;
}

.faq-section {
    max-width: 600px;
    margin: 40px auto;
    font-family: 'Segoe UI', system-ui, sans-serif;
}

.faq-item {
    border-bottom: 1px solid var(--border-color);
    background: #fff;
    transition: background 0.3s ease;
}

/* 1. Eliminar el marcador (flecha) por defecto */
summary {
    list-style: none; /* Estándar */
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px;
    font-weight: 600;
    cursor: pointer;
    color: var(--text-color);
    user-select: none;
}

summary::-webkit-details-marker {
    display: none; /* Específico para Safari/Chrome antiguo */
}

/* 2. Insertar icono personalizado (+ / -) */
summary::after {
    content: '+';
    font-size: 1.5rem;
    font-weight: 400;
    color: var(--primary-blue);
    transition: transform 0.3s ease;
}

/* Cambiar a "-" cuando está abierto */
details[open] summary::after {
    content: '-';
    transform: rotate(180deg);
}

/* 3. Contenido y Transición */
.faq-content {
    padding: 0 20px 20px 20px;
    color: #6b7280;
    line-height: 1.6;
    
    /* Animación de entrada */
    overflow: hidden;
    animation: slideDown 0.3s ease-out;
}

@keyframes slideDown {
    from {
        opacity: 0;
        transform: translateY(-10px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* Estilo visual extra al abrir */
details[open] {
    background-color: #f9fafb;
}

summary:hover {
    color: var(--primary-blue);
}




8. Testimonial carousel

Variables:

{NUMBER_TESTIMONIALS}: Cantidad de testimonios a mostrar.
{PRIMARY_COLOR}: Color de los controles y estrellas.
{FRAMEWORK}: Framework CSS a utilizar (ej. Bootstrap, Tailwind, o CSS puro).

Prompt:
Genera el código para un Carrusel de Testimonios usando {FRAMEWORK}. Debe contener {NUMBER_TESTIMONIALS} tarjetas de testimonios. Cada tarjeta debe incluir: avatar del cliente, nombre, puesto de trabajo, calificación de 5 estrellas (usando el color {PRIMARY_COLOR}) y un texto de reseña. Incluye flechas de navegación a los lados y puntos indicadores en la parte inferior.

Ejemplo de uso:
Genera el código para un Carrusel de Testimonios usando Tailwind CSS. Debe contener 3 tarjetas de testimonios. Cada tarjeta debe incluir: avatar del cliente, nombre, puesto de trabajo, calificación de 5 estrellas (usando el color #F59E0B) y un texto de reseña. Incluye flechas de navegación a los lados y puntos indicadores en la parte inferior.

Código generado esperado:

HTML
<!-- Importar Tailwind CSS y FontAwesome para las flechas -->
<script src="https://cdn.tailwindcss.com"></script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">

<section class="bg-gray-100 py-16 px-4">
    <div class="max-w-5xl mx-auto">
        <h2 class="text-3xl font-bold text-center text-gray-800 mb-12">Lo que dicen nuestros clientes</h2>
        
        <div class="relative group">
            <!-- Contenedor del Carrusel (Scroll Snap) -->
            <div id="carousel" class="flex gap-6 overflow-x-auto scroll-smooth snap-x snap-mandatory no-scrollbar pb-8">
                
                <!-- Tarjeta 1 -->
                <div class="min-w-full md:min-w-[calc(50%-12px)] lg:min-w-[calc(33.333%-16px)] snap-center bg-white p-8 rounded-2xl shadow-sm border border-gray-100">
                    <div class="flex items-center gap-4 mb-4">
                        <img src="https://i.pravatar.cc/150?u=1" alt="Avatar" class="w-14 h-14 rounded-full object-cover border-2 border-blue-500">
                        <div>
                            <h4 class="font-bold text-gray-900">Carlos Mendoza</h4>
                            <p class="text-sm text-gray-500">CTO en TechFlow</p>
                        </div>
                    </div>
                    <!-- Estrellas (#F59E0B es amber-500) -->
                    <div class="flex text-[#F59E0B] mb-4">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
                    </div>
                    <p class="text-gray-600 italic">"La implementación de su software redujo nuestros tiempos de carga en un 40%. El soporte técnico es simplemente excepcional."</p>
                </div>

                <!-- Tarjeta 2 -->
                <div class="min-w-full md:min-w-[calc(50%-12px)] lg:min-w-[calc(33.333%-16px)] snap-center bg-white p-8 rounded-2xl shadow-sm border border-gray-100">
                    <div class="flex items-center gap-4 mb-4">
                        <img src="https://i.pravatar.cc/150?u=2" alt="Avatar" class="w-14 h-14 rounded-full object-cover border-2 border-blue-500">
                        <div>
                            <h4 class="font-bold text-gray-900">Ana Lucía Ríos</h4>
                            <p class="text-sm text-gray-500">Directora de Marketing</p>
                        </div>
                    </div>
                    <div class="flex text-[#F59E0B] mb-4">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
                    </div>
                    <p class="text-gray-600 italic">"Buscábamos una solución escalable y moderna. Superaron nuestras expectativas con una interfaz intuitiva para todo el equipo."</p>
                </div>

                <!-- Tarjeta 3 -->
                <div class="min-w-full md:min-w-[calc(50%-12px)] lg:min-w-[calc(33.333%-16px)] snap-center bg-white p-8 rounded-2xl shadow-sm border border-gray-100">
                    <div class="flex items-center gap-4 mb-4">
                        <img src="https://i.pravatar.cc/150?u=3" alt="Avatar" class="w-14 h-14 rounded-full object-cover border-2 border-blue-500">
                        <div>
                            <h4 class="font-bold text-gray-900">David Webb</h4>
                            <p class="text-sm text-gray-500">Fundador de StartupX</p>
                        </div>
                    </div>
                    <div class="flex text-[#F59E0B] mb-4">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
                    </div>
                    <p class="text-gray-600 italic">"La mejor inversión del año. El panel de analíticas nos permite tomar decisiones basadas en datos reales cada mañana."</p>
                </div>

            </div>

            <!-- Flechas de Navegación -->
            <button onclick="scrollCarousel('left')" class="absolute left-0 top-1/2 -translate-y-1/2 -translate-x-4 bg-white p-3 rounded-full shadow-lg text-gray-800 hover:bg-blue-600 hover:text-white transition-all hidden md:block">
                <i class="fas fa-chevron-left"></i>
            </button>
            <button onclick="scrollCarousel('right')" class="absolute right-0 top-1/2 -translate-y-1/2 translate-x-4 bg-white p-3 rounded-full shadow-lg text-gray-800 hover:bg-blue-600 hover:text-white transition-all hidden md:block">
                <i class="fas fa-chevron-right"></i>
            </button>

            <!-- Puntos Indicadores -->
            <div class="flex justify-center gap-2 mt-4">
                <button onclick="goToSlide(0)" class="dot w-3 h-3 rounded-full bg-blue-600"></button>
                <button onclick="goToSlide(1)" class="dot w-3 h-3 rounded-full bg-gray-300"></button>
                <button onclick="goToSlide(2)" class="dot w-3 h-3 rounded-full bg-gray-300"></button>
            </div>
        </div>
    </div>
</section>

<style>
    /* Ocultar barra de scroll pero mantener funcionalidad */
    .no-scrollbar::-webkit-scrollbar { display: none; }
    .no-scrollbar { -ms-overflow-style: none; scrollbar-width: none; }
</style>

<script>
    const carousel = document.getElementById('carousel');
    const dots = document.querySelectorAll('.dot');

    function scrollCarousel(direction) {
        const scrollAmount = carousel.offsetWidth;
        carousel.scrollBy({
            left: direction === 'left' ? -scrollAmount : scrollAmount,
            behavior: 'smooth'
        });
    }

    function goToSlide(index) {
        const scrollAmount = carousel.offsetWidth;
        carousel.scrollTo({
            left: scrollAmount * index,
            behavior: 'smooth'
        });
    }

    // Actualizar puntos al hacer scroll manual
    carousel.addEventListener('scroll', () => {
        const index = Math.round(carousel.scrollLeft / carousel.offsetWidth);
        dots.forEach((dot, i) => {
            dot.classList.toggle('bg-blue-600', i === index);
            dot.classList.toggle('bg-gray-300', i !== index);
        });
    });
</script>




9. Call-to-Action section

Variables:

{HEADING}: Título del CTA.
{SUBTEXT}: Texto persuasivo debajo del título.
{BTN_TEXT}: Texto del botón.
{BG_THEME}: Estilo de fondo (ej. oscuro, claro, degradado).

Prompt:
Diseña una sección tipo Call-to-Action (CTA) horizontal en HTML y CSS. Usa un tema de fondo {BG_THEME}. Alinea el título "{HEADING}" y el párrafo "{SUBTEXT}" a la izquierda, y coloca un botón de alto contraste con el texto "{BTN_TEXT}" alineado a la derecha (usando Flexbox). Debe tener un padding generoso (ej. 80px) para respirar.

Ejemplo de uso:
Diseña una sección tipo Call-to-Action (CTA) horizontal en HTML y CSS. Usa un tema de fondo degradado azul a morado. Alinea el título "Acelera tu flujo de trabajo" y el párrafo "Únete a más de 10,000 equipos que ya confían en nosotros." a la izquierda, y coloca un botón de alto contraste con el texto "Crear cuenta gratis" alineado a la derecha (usando Flexbox). Debe tener un padding generoso (ej. 80px) para respirar.

Código generado esperado:

HTML
<section class="cta-section">
    <div class="cta-container">
        <!-- Bloque de texto a la izquierda -->
        <div class="cta-content">
            <h2>Acelera tu flujo de trabajo</h2>
            <p>Únete a más de 10,000 equipos que ya confían en nosotros.</p>
        </div>

        <!-- Bloque de acción a la derecha -->
        <div class="cta-action">
            <a href="#" class="btn-high-contrast">Crear cuenta gratis</a>
        </div>
    </div>
</section>

CSS
/* Variables de diseño */
:root {
    --gradient-start: #1A56DB; /* Azul */
    --gradient-end: #7E3AF2;   /* Morado */
    --white: #ffffff;
}

.cta-section {
    /* Degradado azul a morado */
    background: linear-gradient(135deg, var(--gradient-start), var(--gradient-end));
    /* Padding generoso de 80px */
    padding: 80px 20px;
    font-family: 'Inter', system-ui, -apple-system, sans-serif;
    color: var(--white);
}

.cta-container {
    max-width: 1100px;
    margin: 0 auto;
    /* Flexbox para alinear contenido */
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 40px;
}

/* Estilos del texto (Izquierda) */
.cta-content h2 {
    font-size: 2.5rem;
    font-weight: 800;
    margin-bottom: 12px;
    letter-spacing: -0.02em;
}

.cta-content p {
    font-size: 1.25rem;
    opacity: 0.9;
    font-weight: 400;
}

/* Botón de alto contraste (Derecha) */
.btn-high-contrast {
    display: inline-block;
    background-color: var(--white);
    color: var(--gradient-start); /* Texto en azul para contraste */
    padding: 16px 32px;
    border-radius: 12px;
    font-size: 1.1rem;
    font-weight: 700;
    text-decoration: none;
    transition: all 0.3s ease;
    white-space: nowrap; /* Evita que el texto del botón se rompa */
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
}

.btn-high-contrast:hover {
    transform: translateY(-3px);
    box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.2);
    background-color: #f8fafc;
}

/* --- RESPONSIVE --- */
@media (max-width: 768px) {
    .cta-section {
        padding: 60px 20px;
        text-align: center;
    }

    .cta-container {
        flex-direction: column; /* Apilado vertical en móviles */
        gap: 30px;
    }

    .cta-content h2 {
        font-size: 2rem;
    }

    .btn-high-contrast {
        width: 100%;
        max-width: 300px;
    }
}




10. Pricing table

Variables:

{PLAN_NAMES}: Nombres de los planes (ej. Básico, Pro, Empresa).
{CURRENCY}: Moneda (ej. $, €, MXN).
{PRICES}: Precios correspondientes a cada plan.
{HIGHLIGHT_PLAN}: Nombre del plan que debe destacar visualmente.

Prompt:
Construye una tabla de precios (Pricing Table) con HTML y CSS. Genera 3 columnas para los planes: {PLAN_NAMES}. La moneda será {CURRENCY} y los precios mensuales serán {PRICES}. Cada tarjeta debe tener una lista de 4 características. Destaca visualmente el plan "{HIGHLIGHT_PLAN}" haciéndolo ligeramente más grande y aplicando un borde o sombra de distinto color para indicar que es la opción recomendada.

Ejemplo de uso:
Construye una tabla de precios (Pricing Table) con HTML y CSS. Genera 3 columnas para los planes: Básico, Pro, Empresa. La moneda será $ y los precios mensuales serán 9, 29, 99. Cada tarjeta debe tener una lista de 4 características. Destaca visualmente el plan "Pro" haciéndolo ligeramente más grande y aplicando un borde o sombra de distinto color para indicar que es la opción recomendada.

Código generado esperado:

HTML
<section class="pricing-section">
    <div class="pricing-container">
        
        <!-- Plan Básico -->
        <article class="pricing-card">
            <div class="card-header">
                <h3>Básico</h3>
                <div class="price"><span>$</span>9<span>/mes</span></div>
            </div>
            <ul class="features">
                <li><i class="fas fa-check"></i> 1 Proyecto</li>
                <li><i class="fas fa-check"></i> Soporte por Email</li>
                <li><i class="fas fa-check"></i> Acceso a la Comunidad</li>
                <li><i class="fas fa-check"></i> Actualizaciones básicas</li>
            </ul>
            <a href="#" class="btn-outline">Elegir Básico</a>
        </article>

        <!-- Plan Pro (Destacado) -->
        <article class="pricing-card featured">
            <div class="recommended-badge">Más Popular</div>
            <div class="card-header">
                <h3>Pro</h3>
                <div class="price"><span>$</span>29<span>/mes</span></div>
            </div>
            <ul class="features">
                <li><i class="fas fa-check"></i> Proyectos ilimitados</li>
                <li><i class="fas fa-check"></i> Soporte Prioritario 24/7</li>
                <li><i class="fas fa-check"></i> Analíticas avanzadas</li>
                <li><i class="fas fa-check"></i> Exportación de datos</li>
            </ul>
            <a href="#" class="btn-primary">Empezar ahora</a>
        </article>

        <!-- Plan Empresa -->
        <article class="pricing-card">
            <div class="card-header">
                <h3>Empresa</h3>
                <div class="price"><span>$</span>99<span>/mes</span></div>
            </div>
            <ul class="features">
                <li><i class="fas fa-check"></i> Usuarios ilimitados</li>
                <li><i class="fas fa-check"></i> Gestor de cuenta dedicado</li>
                <li><i class="fas fa-check"></i> Seguridad Enterprise</li>
                <li><i class="fas fa-check"></i> API Personalizada</li>
            </ul>
            <a href="#" class="btn-outline">Contactar Ventas</a>
        </article>

    </div>
</section>

<!-- Iconos para los checkmarks -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">

CSS
:root {
    --primary: #1A56DB;
    --text-main: #1f2937;
    --text-muted: #6b7280;
    --white: #ffffff;
    --bg-light: #f9fafb;
}

.pricing-section {
    background-color: var(--bg-light);
    padding: 100px 20px;
    font-family: 'Inter', system-ui, sans-serif;
}

.pricing-container {
    max-width: 1100px;
    margin: 0 auto;
    display: flex;
    justify-content: center;
    align-items: center; /* Centra verticalmente para que el destacado sobresalga */
    gap: 20px;
}

.pricing-card {
    background: var(--white);
    padding: 40px 30px;
    border-radius: 20px;
    border: 1px solid #e5e7eb;
    flex: 1;
    max-width: 350px;
    display: flex;
    flex-direction: column;
    text-align: center;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

/* --- Estilos del Plan Destacado (PRO) --- */
.pricing-card.featured {
    position: relative;
    transform: scale(1.08); /* Más grande */
    border: 2px solid var(--primary);
    box-shadow: 0 20px 25px -5px rgba(26, 86, 219, 0.15);
    z-index: 10;
}

.recommended-badge {
    position: absolute;
    top: -15px;
    left: 50%;
    transform: translateX(-50%);
    background: var(--primary);
    color: white;
    padding: 5px 15px;
    border-radius: 20px;
    font-size: 0.85rem;
    font-weight: 700;
}

/* --- Cabecera y Precios --- */
.card-header h3 {
    font-size: 1.5rem;
    color: var(--text-main);
    margin-bottom: 20px;
}

.price {
    font-size: 3rem;
    font-weight: 800;
    color: var(--text-main);
    margin-bottom: 30px;
}

.price span:first-child { font-size: 1.5rem; vertical-align: super; }
.price span:last-child { font-size: 1rem; color: var(--text-muted); font-weight: 400; }

/* --- Lista de Características --- */
.features {
    list-style: none;
    padding: 0;
    margin: 0 0 40px 0;
    text-align: left;
}

.features li {
    margin-bottom: 15px;
    color: var(--text-muted);
    font-size: 0.95rem;
    display: flex;
    align-items: center;
    gap: 10px;
}

.features i {
    color: #10b981; /* Verde para los checks */
}

/* --- Botones --- */
.btn-primary, .btn-outline {
    padding: 12px 25px;
    border-radius: 10px;
    text-decoration: none;
    font-weight: 600;
    transition: 0.3s;
    margin-top: auto; /* Empuja el botón al final de la tarjeta */
}

.btn-primary {
    background: var(--primary);
    color: white;
}

.btn-outline {
    border: 1.5px solid var(--primary);
    color: var(--primary);
}

.btn-outline:hover {
    background: var(--primary);
    color: white;
}

/* --- Responsive --- */
@media (max-width: 900px) {
    .pricing-container {
        flex-direction: column;
        align-items: center;
        gap: 40px;
    }
    
    .pricing-card.featured {
        transform: scale(1); /* Quitamos el escalado en móvil para evitar solapamientos */
    }
}



