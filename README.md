# sito-scuola
<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ITTS "O.Belluzzi L.Da Vinci"</title>
    
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700;800&family=Roboto:wght@300;400;500&family=Share+Tech+Mono&display=swap" rel="stylesheet">
    <link rel="icon" type="image/png" href="IMG/images.png"/>

    <style>
        :root {
            --navy-deep: #021a24;     /* Blu abisso */
            --navy-mid: #064e6b;      /* Blu scafo */
            --ocean-bright: #0096c7;  /* Azzurro acqua */
            --tech-cyan: #00f2ff;     /* Ciano neon (Tech) */
            --alert-orange: #ff6b00;  /* Arancione salvagente */
            --steel-grey: #e9ecef;
        }

        body { font-family: 'Roboto', sans-serif; background-color: #f8f9fa; overflow-x: hidden; }
        h1, h2, h3, h4, h5 { font-family: 'Montserrat', sans-serif; }
        
        /* --- 1. TOP BAR --- */
        .top-bar { background-color: var(--navy-deep); color: #8fa6b0; font-size: 0.8rem; ; border-bottom: 2px solid var(--ocean-bright); }
        .top-bar a { color: #fff; text-decoration: none; margin-left: 15px; transition: color 0.2s; }
        .top-bar a:hover { color: var(--tech-cyan); }

        /* --- 2. HEADER --- */
        .main-header { background: #fff; padding: 25px 0; }
        .school-logo img {
            height: 120px; /* Regola questo numero per ingrandire il logo. 120px è bello grande come nella foto */
            width: auto;   /* Mantiene le proporzioni (non lo stira) */
            object-fit: contain;
        }

        @media (max-width: 768px) {
            .school-logo img {
                height: 80px; /* Più piccolo su mobile */
            }
            .school-name h2 {
                font-size: 1.4rem !important; /* Testo più piccolo su mobile */
            }
        }
        .school-name h1 { font-size: 1.1rem; color: #666; font-weight: 600; margin: 0; letter-spacing: 1px; }
        .school-name h2 { font-size: 1.8rem; color: var(--navy-deep); font-weight: 800; margin: 0; text-transform: uppercase; }
        .header-search { color: var(--navy-mid); cursor: pointer; }

        /* --- 3. MENU --- */
        .nav-main { padding: 10px 0; font-weight: 700; font-size: 1.15rem; }
        .nav-link-custom { margin-right: 25px; text-decoration: none; position: relative; }
        .nav-link-custom::after { content: ''; position: absolute; width: 0; height: 3px; bottom: -5px; left: 0; transition: width 0.3s; }
        .nav-link-custom:hover::after { width: 100%; }

        /* Colori Menu simili a Rimini ma tonalità marine */
        .c-scuola { color: #d62828; } .c-scuola:hover::after { background: #d62828; }
        .c-servizi { color: #0096c7; } .c-servizi:hover::after { background: #0096c7; }
        .c-novita { color: #2a9d8f; } .c-novita:hover::after { background: #2a9d8f; }
        .c-didattica { color: #4361ee; } .c-didattica:hover::after { background: #4361ee; }

        .sub-nav { border-bottom: 1px solid #ddd; padding-bottom: 10px; margin-bottom: 0; }
        .sub-nav a { color: #555; text-decoration: none; font-size: 0.9rem; margin-right: 20px; font-weight: 500; }
        .sub-nav a:hover { color: var(--ocean-bright); }

        /* --- 4. ALERT BAR --- */
        .alert-bar {
            background: linear-gradient(90deg, var(--ocean-bright) 0%, var(--navy-mid) 100%);
            color: white; padding: 15px; text-align: center; font-size: 1.1rem; font-weight: 500;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1); z-index: 10; position: relative;
        }

        /* --- 5. HERO SECTION (Split) --- */
        .hero-container { display: flex; flex-wrap: wrap; min-height: 450px; }
        
        /* Sinistra */
        .hero-left {
            width: 50%; background: var(--navy-deep); color: white; padding: 60px;
            position: relative; display: flex; flex-direction: column; justify-content: center;
            overflow: hidden;
        }
        /* Background decorativo mappa nautica */
        .hero-left::before {
            content: ''; position: absolute; top:0; left:0; width: 100%; height: 100%;
            background-image: radial-gradient(circle, rgba(255,255,255,0.05) 1px, transparent 1px);
            background-size: 30px 30px; opacity: 0.5;
        }
        .hero-title { font-size: 3.5rem; line-height: 1; margin-bottom: 20px; z-index: 2; }
        .hero-subtitle { font-family: 'Share Tech Mono', monospace; color: var(--tech-cyan); letter-spacing: 2px; margin-bottom: 10px; }
        .btn-hero {
            border: 2px solid var(--tech-cyan); color: var(--tech-cyan); padding: 10px 25px;
            text-decoration: none; font-weight: bold; width: fit-content; margin-top: 20px;
            transition: all 0.3s; z-index: 2; text-transform: uppercase; border-radius: 5px;
        }
        .btn-hero:hover { background: var(--tech-cyan); color: var(--navy-deep); box-shadow: 0 0 15px var(--tech-cyan); }

        /* Destra (Radar Tech) */
        .hero-right {
            width: 50%; background: #000; position: relative; overflow: hidden;
            display: flex; align-items: center; justify-content: center;
        }
        /* Effetto griglia sonar verde/blu */
        .grid-bg {
            position: absolute; width: 200%; height: 200%;
            background: linear-gradient(rgba(0, 242, 255, 0.1) 1px, transparent 1px),
                        linear-gradient(90deg, rgba(0, 242, 255, 0.1) 1px, transparent 1px);
            background-size: 40px 40px;
            transform: perspective(500px) rotateX(60deg) translateY(-100px) translateZ(-200px);
            animation: moveGrid 5s linear infinite;
        }
        
        /* Cerchio Radar */
        .radar-scope {
            width: 300px; height: 300px; border: 3px solid rgba(0, 242, 255, 0.5); border-radius: 50%;
            position: relative; background: radial-gradient(circle, rgba(0, 242, 255, 0.1), transparent 70%);
            box-shadow: 0 0 20px rgba(0, 242, 255, 0.2);
            z-index: 5;
        }
        .radar-sweep {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%; border-radius: 50%;
            background: conic-gradient(from 0deg, transparent 270deg, rgba(0, 242, 255, 0.6) 360deg);
            animation: scan 4s infinite linear;
        }
        .radar-blip {
            position: absolute; width: 10px; height: 10px; background: #ff0055; border-radius: 50%;
            top: 30%; right: 30%; box-shadow: 0 0 10px #ff0055; animation: blink 2s infinite;
        }
        .tech-overlay-text {
            position: absolute; bottom: 30px; width: 100%; text-align: center;
            font-family: 'Share Tech Mono', monospace; color: white; text-shadow: 0 0 5px white; z-index: 10;
        }

        /* --- 6. LINK RAPIDI (Plancia) --- */
        .quick-links-section { padding: 40px 0; background-color: white; margin-top: -30px; position: relative; z-index: 10; border-radius: 10px 10px 0 0; box-shadow: 0 -5px 20px rgba(0,0,0,0.05); }
        .quick-card {
            text-align: center; padding: 20px; transition: transform 0.3s;
            border: 1px solid #eee; border-radius: 8px; height: 100%; background: #fff;
        }
        .quick-card:hover { transform: translateY(-5px); border-color: var(--ocean-bright); box-shadow: 0 10px 20px rgba(0,150,199,0.15); }
        .icon-box {
            width: 70px; height: 70px; background: var(--steel-grey); border-radius: 50%; margin: 0 auto 15px;
            display: flex; align-items: center; justify-content: center; font-size: 1.8rem; color: var(--navy-mid);
            transition: all 0.3s;
        }
        .quick-card:hover .icon-box { background: var(--navy-mid); color: var(--tech-cyan); }
        
        /* --- 7. NEWS GRID --- */
        .news-section { padding: 60px 0; background-color: #f1f4f6; }
        .news-title { border-left: 5px solid var(--alert-orange); padding-left: 15px; margin-bottom: 30px; color: var(--navy-deep); font-weight: 700; }
        .news-card { border: none; border-radius: 0; transition: shadow 0.3s; }
        .news-card img { height: 200px; object-fit: cover; filter: brightness(0.9); transition: 0.3s; }
        .news-card:hover img { filter: brightness(1.1); }
        .news-date { color: var(--ocean-bright); font-weight: bold; font-size: 0.85rem; margin-top: 10px; }
        .news-content { padding: 15px; background: white; border-bottom: 3px solid transparent; }
        .news-card:hover .news-content { border-bottom: 3px solid var(--alert-orange); }

        /* --- 8. FOOTER --- */
        footer { background: var(--navy-deep); color: #ccc; margin-top: 0; padding-top: 50px; position: relative; }
        .footer-wave {
            position: absolute; top: -40px; left: 0; width: 100%; height: 40px;
            background: url('data:image/svg+xml;utf8,<svg viewBox="0 0 1440 320" xmlns="http://www.w3.org/2000/svg"><path fill="%23021a24" fill-opacity="1" d="M0,224L48,213.3C96,203,192,181,288,181.3C384,181,480,203,576,224C672,245,768,267,864,261.3C960,256,1056,224,1152,202.7C1248,181,1344,171,1392,165.3L1440,160L1440,320L1392,320C1344,320,1248,320,1152,320C1056,320,960,320,864,320C768,320,672,320,576,320C480,320,384,320,288,320C192,320,96,320,48,320L0,320Z"></path></svg>');
            background-size: cover; background-repeat: no-repeat;
        }
        footer h5 { color: white; border-bottom: 2px solid var(--ocean-bright); padding-bottom: 10px; display: inline-block; margin-bottom: 20px; }
        footer a { color: #aab; text-decoration: none; display: block; margin-bottom: 8px; transition: 0.3s; }
        footer a:hover { color: var(--tech-cyan); padding-left: 5px; }
        .footer-bottom { background: #000; padding: 20px 0; text-align: center; font-size: 0.8rem; margin-top: 40px; }

        /* Animations */
        @keyframes scan { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }
        @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }
        @keyframes moveGrid { 0% { background-position: 0 0; } 100% { background-position: 0 40px; } }
        
        @media (max-width: 768px) { .hero-left, .hero-right { width: 100%; min-height: 300px; } }
        /* --- INCOLLA QUESTO DENTRO <STYLE>, IN FONDO --- */

        /* Rende l'header appiccicoso */
        .main-header {
            position: sticky;
            top: 0;
            z-index: 1020; /* Sopra a tutto */
            background: white;
            transition: all 0.3s ease; /* Animazione morbida */
            width: 100%;
        }

        /* Quando si scorre, questa classe si attiva */
        .main-header.scrolled {
            padding-top: 5px !important;
            padding-bottom: 5px !important;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1); /* Ombra sotto */
            border-bottom: none !important;
        }

        /* Rimpicciolisce il logo */
        .main-header.scrolled .school-logo img {
            height: 50px !important; /* Diventa piccolo */
            transition: height 0.3s ease;
        }

        /* Nasconde le scritte grandi per fare spazio */
        .main-header.scrolled .school-name h2,
        .main-header.scrolled .school-name h4,
        .main-header.scrolled .badge,
        .main-header.scrolled .text-muted.small { 
            /* Nasconde: Titolo grande, sottotitolo, badge, e scritta social */
            display: none !important; 
        }

        /* Mostra solo il nome essenziale quando rimpicciolito (opzionale, se vuoi) */
        .main-header.scrolled .school-name::after {
            content: "ITTS O.BELLUZZI L.DA VINCI";
            font-weight: 800;
            font-size: 1.2rem;
            color: #002b36;
        }
        .nav-colored a { 
            text-decoration: none; 
            margin-right: 25px; 
            font-weight: 700; 
            font-size: 1.1rem;
            text-transform: uppercase;
        }
        .c-red { color: #dc3545; }
        .c-cyan { color: #0096c7; }
        .c-green { color: #2a9d8f; }
        .c-blue { color: #4361ee; }

        /* Questa regola serve per nascondere il menu quando scorri (OPZIONALE) */
        /* Se vuoi che il menu RESTI VISIBILE anche quando scorri, NON mettere questo codice sotto. */
        /* Se invece vuoi che sparisca per risparmiare spazio, aggiungilo: */
        .main-header.scrolled .nav-colored {
            display: none;
        }
        /* --- FIX DIMENSIONI IMMAGINI (AGGIUNGI QUESTO) --- */

        /* 1. Sistema le immagini delle News */
        /* Seleziona l'immagine dentro la card delle news */
        .news-card .card-img-top {
            height: 200px !important; /* FORZA l'altezza a 200 pixel. Il "!important" è fondamentale qui. */
            width: 100%;              /* Si adatta alla larghezza della colonna */
            object-fit: cover;        /* Ritaglia l'immagine se non è delle proporzioni giuste, invece di schiacciarla */
        }

        /* 2. Sistema i loghi nel Footer */
        /* Seleziona le immagini dentro la colonna dei partner nel footer */
        footer .d-flex.flex-wrap.gap-2 img {
            max-height: 50px !important; /* Altezza massima 50 pixel (piccoli) */
            width: auto;                 /* Mantiene le proporzioni */
            border: 1px solid rgba(255,255,255,0.2); /* (Opzionale) Aggiunge un bordino elegante */
        }
        /* --- STILE SEZIONE INDIRIZZI --- */

        /* Colore di sfondo leggero per staccare dalla sezione precedente */
        .bg-light { background-color: #f8f9fa !important; }

        /* La scatola (Card) dell'indirizzo */
        .course-card {
            transition: transform 0.3s ease, box-shadow 0.3s ease; /* Animazione morbida */
            border: 1px solid #eee;
        }

        /* Effetto quando passi il mouse sopra (Hover) */
        .course-card:hover {
            transform: translateY(-10px); /* Si alza di 10 pixel */
            box-shadow: 0 10px 20px rgba(0,0,0,0.1) !important; /* L'ombra diventa più forte */
            border-color: #0077be; /* Il bordo diventa azzurro */
        }

        /* Stile delle Icone (Ancora, Chip, ecc.) */
        .icon-box i {
            color: #002b36; /* Blu Scuro Navale */
            transition: color 0.3s;
        }

        /* Quando passi il mouse sulla card, l'icona diventa azzurra */
        .course-card:hover .icon-box i {
            color: #0077be;
        }

        /* Colore del titolo */
        .text-navy { color: #002b36; }
        /* Definizione del movimento */
        @keyframes galleggia {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-8px); } /* Va su di 10 pixel */
            100% { transform: translateY(0px); }
        }

        /* Applica il movimento alle icone */
        .icon-box i {
            animation: galleggia 3s ease-in-out infinite; /* Si muove all'infinito ogni 3 secondi */
        }

        /* Se vuoi che si muovano a tempi diversi (più naturale) */
        .col-md-6:nth-child(even) .icon-box i {
            animation-delay: 1.5s; /* Le icone pari partono dopo */
        }
        /* --- STILE ONDA --- */
        .ocean-wave {
            position: relative;
            width: 100%;
            line-height: 0; /* Fondamentale: toglie una riga bianca fastidiosa sotto */
            background-color: #1a1a1a; /* DEVE essere identico al colore di sfondo della tua Hero Section */
            margin-top: -1px; /* Corregge eventuali filetti bianchi tra le sezioni */
        }

        .ocean-wave svg {
            position: relative;
            display: block;
            width: calc(100% + 1.3px);
            height: 80px; /* Altezza dell'onda, puoi cambiarla */
        }

        .ocean-wave path {
            fill: #f8f9fa; /* Colore dell'onda: metti #ffffff se sotto è bianco, o #f8f9fa se è grigio chiaro */
        }
    </style>
</head>
<body>

    <div class="top-bar">
        <div class="container d-flex justify-content-between">
            <span><i class="fas fa-anchor me-2"></i>Ministero dell'Istruzione e del Merito</span>
            <div>
                <a href="#"><i class="fas fa-user-astronaut me-1"></i> Area Riservata</a>
                <a href="#"><i class="fas fa-globe me-1"></i> English</a>
            </div>
        </div>
    </div>

    <header id="myHeader" class="main-header py-4 border-bottom">
        <div class="container">
            
            <div class="d-flex justify-content-between align-items-center">
                
                <div class="d-flex align-items-center">
                    <div class="school-logo me-4">
                        <img src="IMG/images.png" alt="Logo Scuola" style="height: 110px; width: auto; transition: height 0.3s;">
                    </div>
                    <div class="school-name">
                        <h4 style="font-size: 1.1rem; color: #666; font-weight: 500; margin-bottom: 0;">Istituto Tecnico Tecnologico Statale</h4>
                        <h2 style="font-size: 2.2rem; color: #001f29; font-weight: 800; margin: 0; line-height: 1.2;">ITTS "O.BELLUZZI L.DA VINCI"</h2>
                        <span class="badge bg-primary rounded-0 mt-2 px-3 py-1">RIMINI</span>
                    </div>
                </div>

                <div class="text-end search-social-block">
                    <div class="input-group mb-2 justify-content-end">
                        <input type="text" class="form-control" placeholder="Cerca nel sito..." style="max-width: 250px; border-right: none;">
                        <button class="btn btn-outline-secondary" type="button" style="border-left: none;">
                            <i class="fas fa-search"></i>
                        </button>
                    </div>
                    <div class="text-muted small">
                        Seguici: 
                        <a href="#" class="text-dark ms-2 fs-5"><i class="fab fa-instagram"></i></a>
                        <a href="#" class="text-dark ms-2 fs-5"><i class="fab fa-facebook"></i></a>
                    </div>
                </div>

            </div>
            <div class="row border-top pt-3">
                <div class="col-12">
                    <nav class="nav-colored d-flex flex-wrap">
                        <a href="#" class="c-red">L'ISTITUTO</a>
                        <a href="#" class="c-cyan">SERVIZI</a>
                        <a href="#" class="c-green">NOVITÀ</a>
                        <a href="#" class="c-blue">DIDATTICA</a>
                    </nav>
                </div>
            </div>
        </div>
    </header>
    <div class="container mb-3">
        <nav class="sub-nav d-flex flex-wrap">
            <a href="#">Studenti/Famiglie</a>
            <a href="#">Personale Docente</a>
            <a href="#">Personale ATA</a>
            <a href="#">Sicurezza a Bordo</a>
            <a href="#">Albo Online</a>
            <a href="#">PCTO (Alternanza)</a>
        </nav>
    </div>

    <div class="alert-bar">
        <i class="fas fa-bullhorn me-2"></i> ISCRIZIONI A.S. 2026/2027 APERTE
        <a href="#" class="btn btn-sm btn-outline-light ms-3 rounded-pill">VAI AL PORTALE <i class="fas fa-arrow-right"></i></a>
    </div>

    <div class="hero-container">
        <div class="hero-left">
            <div class="hero-subtitle"><i class="fas fa-satellite-dish"></i> SISTEMI ATTIVI</div>
            <h1 class="hero-title">IL TUO FUTURO<br>HA UNA ROTTA<br>SICURA.</h1>
            <p class="lead text-white-50">Informatica, Meccanica,Elettronica,Grafica... La tecnologia incontra il mare.</p>
            <a href="#" class="btn-hero">ESPLORA I CORSI</a>
        </div>
        
        <div class="hero-right">
            <div class="grid-bg"></div>
            <div class="radar-scope">
                <div class="radar-sweep"></div>
                <div class="radar-blip"></div>
            </div>

            <div class="tech-overlay-text">
                SCANNING SECTOR 04...<br>
                <span style="color:var(--tech-cyan)">TARGET ACQUIRED: FUTURE STUDENTS</span>
            </div>
        </div>
        <div class="ocean-wave" style="height: 100px; overflow: hidden;">
            <svg viewBox="0 0 500 150" preserveAspectRatio="none" style="height: 100%; width: 100%;">
                <path d="M0.00,49.98 C149.99,150.00 349.20,-49.98 500.00,49.98 L500.00,150.00 L0.00,150.00 Z" style="stroke: none; fill: #ffffff;"></path>
            </svg>
        </div>
    </div>

    <div class="container quick-links-section">
        <div class="row g-4">
            <div class="col-6 col-md-3">
                <div class="quick-card">
                    <div class="icon-box"><i class="fas fa-laptop-code"></i></div>
                    <h5>Registro Elettronico</h5>
                </div>
            </div>
            <div class="col-6 col-md-3">
                <div class="quick-card">
                    <div class="icon-box"><i class="far fa-clock"></i></div>
                    <h5>Orario Lezioni</h5>
                </div>
            </div>
            <div class="col-6 col-md-3">
                <div class="quick-card">
                    <div class="icon-box"><i class="fas fa-file-contract"></i></div>
                    <h5>Circolari</h5>
                </div>
            </div>
            <div class="col-6 col-md-3">
                <div class="quick-card">
                    <div class="icon-box"><i class="fas fa-map-marked-alt"></i></div>
                    <h5>Dove Siamo</h5>
                </div>
            </div>
        </div>
    </div>

    <section class="news-section">
        <div class="container">
            <h3 class="news-title">DAL DIARIO DI BORDO</h3>
            <div class="row g-4">
                <div class="col-md-4">
                    <div class="card news-card h-100">
                        <img src="IMG/Gear-VR-with-Controller.jpg" class="card-img-top" alt="Nave">
                        <div class="news-content">
                            <div class="news-date">12 FEB 2026</div>
                            <h5 class="card-title mt-2">Varo del simulatore navale 4.0</h5>
                            <p class="card-text text-muted small">Inaugurato il nuovo laboratorio con tecnologia VR.</p>
                            <a href="#" class="text-decoration-none fw-bold text-dark">LEGGI <i class="fas fa-chevron-right"></i></a>
                        </div>
                    </div>
                </div>
                <div class="col-md-4">
                    <div class="card news-card h-100">
                        <img src="https://images.unsplash.com/photo-1581091226825-a6a2a5aee158?auto=format&fit=crop&q=80&w=800" class="card-img-top" alt="Tech">
                        <div class="news-content">
                            <div class="news-date">10 FEB 2026</div>
                            <h5 class="card-title mt-2">Hackathon della Logistica</h5>
                            <p class="card-text text-muted small">La 5^B vince il premio regionale con un progetto sui droni portuali.</p>
                            <a href="#" class="text-decoration-none fw-bold text-dark">LEGGI <i class="fas fa-chevron-right"></i></a>
                        </div>
                    </div>
                </div>
                <div class="col-md-4">
                    <div class="card news-card h-100">
                        <img src="https://images.unsplash.com/photo-1541829070764-84a7d30dd3f3?auto=format&fit=crop&q=80&w=800" class="card-img-top" alt="Mare">
                        <div class="news-content">
                            <div class="news-date">05 FEB 2026</div>
                            <h5 class="card-title mt-2">Uscita in mare classi prime</h5>
                            <p class="card-text text-muted small">Prima esperienza di navigazione sulla nave scuola "Poseidon".</p>
                            <a href="#" class="text-decoration-none fw-bold text-dark">LEGGI <i class="fas fa-chevron-right"></i></a>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="text-center mt-5">
                <a href="#" class="btn btn-outline-dark rounded-0 px-4">TUTTE LE NOTIZIE</a>
            </div>
        </div>
    </section>

    <section class="courses-section py-5 bg-light">
        <div class="container">
            
            <div class="text-center mb-5">
                <h3 class="fw-bold" style="color: #002b36; letter-spacing: 1px;">LA NOSTRA OFFERTA FORMATIVA</h3>
                <div style="height: 3px; width: 60px; background: #0077be; margin: 10px auto;"></div>
                <p class="text-muted">Scopri i percorsi tecnici per il tuo futuro professionale</p>
            </div>

            <div class="row g-4">

                <div class="col-md-6 col-lg-3">
                    <div class="course-card text-center p-4 h-100 bg-white shadow-sm rounded">
                        <div class="icon-box mb-3">
                            <i class="fas fa-flask fa-3x"></i>
                        </div>
                        <h5 class="fw-bold text-navy">Chimica, Materiali e Biotecnologie</h5>
                        <p class="small text-muted mb-4">Studio dei processi chimici, analisi di laboratorio e scienze dei materiali innovativi.</p>
                        <a href="#" class="btn btn-outline-primary btn-sm rounded-pill px-4">Scopri</a>
                    </div>
                </div>

                <div class="col-md-6 col-lg-3">
                    <div class="course-card text-center p-4 h-100 bg-white shadow-sm rounded">
                        <div class="icon-box mb-3">
                            <i class="fas fa-microchip fa-3x"></i>
                        </div>
                        <h5 class="fw-bold text-navy">Elettronica ed elettrotecnica</h5>
                        <p class="small text-muted mb-4">Studio dei circuiti elettrici, elettronici, dei sistemi automatici e programmazione di microcontrollori.</p>
                        <a href="#" class="btn btn-outline-primary btn-sm rounded-pill px-4">Scopri</a>
                    </div>
                </div>

                <div class="col-md-6 col-lg-3">
                    <div class="course-card text-center p-4 h-100 bg-white shadow-sm rounded">
                        <div class="icon-box mb-3">
                            <i class="fas fa-laptop-code fa-3x"></i>
                        </div>
                        <h5 class="fw-bold text-navy">Informatica e Telecomunicazioni</h5>
                        <p class="small text-muted mb-4">Sviluppo software, reti, cybersecurity e gestione dei dati. Il futuro digitale inizia qui.</p>
                        <a href="#" class="btn btn-outline-primary btn-sm rounded-pill px-4">Scopri</a>
                    </div>
                </div>

                <div class="col-md-6 col-lg-3">
                    <div class="course-card text-center p-4 h-100 bg-white shadow-sm rounded">
                        <div class="icon-box mb-3">
                            <i class="fas fa-cogs fa-3x"></i>
                        </div>
                        <h5 class="fw-bold text-navy">Meccanica e Meccatronica</h5>
                        <p class="small text-muted mb-4">Progettazione e funzionamento di macchine, impianti e sistemi energetici.</p>
                        <a href="#" class="btn btn-outline-primary btn-sm rounded-pill px-4">Scopri</a>
                    </div>
                </div>
                <div class="col-md-6 col-lg-3">
                    <div class="course-card text-center p-4 h-100 bg-white shadow-sm rounded">
                        <div class="icon-box mb-3">
                            <i class="fas fa-palette fa-3x"></i>
                        </div>
                        <h5 class="fw-bold text-navy">Grafica e Comunicazione</h5>
                        <p class="small text-muted mb-4">Progettazione multimediale, fotografia, video editing e design per la comunicazione visiva.</p>
                        <a href="#" class="btn btn-outline-primary btn-sm rounded-pill px-4">Scopri</a>
                    </div>
                </div>
                <div class="col-md-6 col-lg-3">
                    <div class="course-card text-center p-4 h-100 bg-white shadow-sm rounded">
                        <div class="icon-box mb-3">
                            <i class="fas fa-hard-hat fa-3x"></i>
                        </div>
                        <h5 class="fw-bold text-navy">Costruzioni, Ambiente e Territorio</h5>
                        <p class="small text-muted mb-4">Progettazione edilizia, topografia, sicurezza nei cantieri ed efficienza energetica (ex Geometra).</p>
                        <a href="#" class="btn btn-outline-primary btn-sm rounded-pill px-4">Scopri</a>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <footer>
        <div class="footer-wave"></div>
        <div class="container position-relative z-1">
            <div class="row">
                <div class="col-md-4 mb-4">
                    <h5 class="text-uppercase">ITTS "O.Belluzzi L.Da Vinci"</h5>
                    <p class="small text-secondary">
                        L'eccellenza nella formazione tecnologica.<br>
                        Prepariamo i comandanti e i tecnici del domani.
                    </p>
                    <p class="mt-3">
                        <i class="fas fa-map-marker-alt me-2 text-info"></i> Via Ada Negri 34, Rimini<br>
                        <i class="fas fa-phone me-2 text-info"></i> +39 0541 123456<br>
                        <i class="fas fa-envelope me-2 text-info"></i> segreteria@ittsrimini.edu.it
                    </p>
                </div>
                
                <div class="col-md-4 mb-4">
                    <h5 class="text-uppercase">Trasparenza</h5>
                    <ul class="list-unstyled">
                        <li><a href="#">Amministrazione Trasparente</a></li>
                        <li><a href="#">Albo Pretorio Online</a></li>
                        <li><a href="#">Accessibilità (Legge Stanca)</a></li>
                        <li><a href="#">Privacy Policy & GDPR</a></li>
                        <li><a href="#">Note Legali</a></li>
                    </ul>
                </div>
                
                <div class="col-md-4 mb-4">
                    <h5 class="text-uppercase">Progetti & Partner</h5>
                    <div class="d-flex flex-wrap gap-2">
                        <img src="IMG/pon-FSER-sito-1024x768-1.jpg" alt="PON" class="rounded">
                        <img src="IMG/Flag_of_Europe.svg.webp" alt="Unione Europea" class="rounded">
                        <img src="IMG/Logo_MIM_1.png" alt="Ministero" class="rounded">
    
                    </div>
                    <div class="mt-4">
                        <h6 class="text-white">Orari Segreteria:</h6>
                        <span class="small text-secondary">Lun-Ven: 08:00 - 13:00<br>Sab: 08:00 - 12:00</span>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="footer-bottom">
            <div class="container">
                &copy; 2026 ITTS "O.Belluzzi L.Da Vinci" - Tutti i diritti riservati<br>
                
                <div class="mt-2">
                    Sito progettato e sviluppato da: <strong class="text-white">Alam - Zamagni</strong>
                </div>
            </div>
        </div>
    </footer>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>

    <script>
    // Seleziona l'header
        const header = document.getElementById('myHeader');
    
     // Ascolta lo scorrimento
        window.addEventListener('scroll', function() {
            if (window.scrollY > 50) { 
                // Se scorri giù di 50 pixel, attiva la modalità compatta
                header.classList.add('scrolled');
                header.classList.remove('py-4'); // Toglie il padding grosso
            } else {
                // Se torni in cima, rimetti tutto normale
                header.classList.remove('scrolled');
                header.classList.add('py-4'); // Rimette il padding grosso
            }
        });
    </script>
</body>
</html>

