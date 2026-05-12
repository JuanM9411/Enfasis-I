<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Aprendiendo con Juego: IA para Educadores</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;1,9..40,300&display=swap" rel="stylesheet">
<style>
  :root {
    --azul: #1B4FD8;
    --azul-claro: #4F7FFF;
    --azul-oscuro: #0D2B7A;
    --verde: #0B8A5A;
    --verde-claro: #12C27A;
    --ambar: #C25A0B;
    --ambar-claro: #F28C38;
    --morado: #5B21B6;
    --morado-claro: #8B5CF6;
    --fondo: #F0F4FF;
    --fondo2: #E8EEFF;
    --blanco: #FFFFFF;
    --texto: #0D1B3E;
    --texto2: #3A4A6B;
    --texto3: #6B7BA0;
    --borde: rgba(27,79,216,0.15);
    --sombra: 0 4px 24px rgba(27,79,216,0.12);
    --sombra2: 0 8px 40px rgba(27,79,216,0.18);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--fondo);
    color: var(--texto);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* FONDO ANIMADO */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background:
      radial-gradient(ellipse 80% 60% at 10% 10%, rgba(79,127,255,0.12) 0%, transparent 60%),
      radial-gradient(ellipse 60% 50% at 90% 80%, rgba(18,194,122,0.10) 0%, transparent 60%),
      radial-gradient(ellipse 50% 40% at 50% 50%, rgba(139,92,246,0.06) 0%, transparent 70%);
    pointer-events: none;
    z-index: 0;
  }

  /* GRID DE FONDO */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(27,79,216,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(27,79,216,0.04) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .wrapper {
    position: relative;
    z-index: 1;
    max-width: 1100px;
    margin: 0 auto;
    padding: 2rem 1.5rem 4rem;
  }

  /* ===== HERO ===== */
  .hero {
    background: linear-gradient(135deg, var(--azul-oscuro) 0%, var(--azul) 50%, var(--azul-claro) 100%);
    border-radius: 24px;
    padding: 3rem 3rem 2.5rem;
    margin-bottom: 1.5rem;
    position: relative;
    overflow: hidden;
    box-shadow: var(--sombra2);
    animation: slideDown 0.7s cubic-bezier(0.22,1,0.36,1) both;
  }

  .hero::before {
    content: '';
    position: absolute;
    top: -60px; right: -60px;
    width: 300px; height: 300px;
    background: rgba(255,255,255,0.05);
    border-radius: 50%;
  }

  .hero::after {
    content: '';
    position: absolute;
    bottom: -80px; left: 30%;
    width: 400px; height: 200px;
    background: rgba(255,255,255,0.04);
    border-radius: 50%;
  }

  .hero-tag {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    background: rgba(255,255,255,0.15);
    border: 1px solid rgba(255,255,255,0.25);
    border-radius: 100px;
    padding: 5px 14px;
    font-size: 12px;
    color: rgba(255,255,255,0.9);
    font-family: 'Syne', sans-serif;
    font-weight: 600;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    margin-bottom: 1.25rem;
  }

  .hero-tag svg { width: 14px; height: 14px; }

  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(1.8rem, 4vw, 2.8rem);
    font-weight: 800;
    color: #fff;
    line-height: 1.15;
    margin-bottom: 0.75rem;
    position: relative;
    z-index: 1;
  }

  .hero h1 span {
    background: linear-gradient(90deg, #A8FFDD, #C4E0FF);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-sub {
    font-size: 15px;
    color: rgba(255,255,255,0.75);
    font-weight: 300;
    margin-bottom: 2rem;
    max-width: 580px;
    position: relative;
    z-index: 1;
  }

  .hero-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    position: relative;
    z-index: 1;
  }

  .pill {
    display: inline-flex;
    align-items: center;
    gap: 5px;
    background: rgba(255,255,255,0.12);
    border: 1px solid rgba(255,255,255,0.2);
    border-radius: 100px;
    padding: 6px 14px;
    font-size: 13px;
    color: rgba(255,255,255,0.9);
    font-weight: 400;
  }

  .pill svg { width: 13px; height: 13px; opacity: 0.8; }

  /* ===== MÉTRICAS ===== */
  .metrics-row {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 12px;
    margin-bottom: 1.5rem;
    animation: fadeUp 0.7s 0.15s cubic-bezier(0.22,1,0.36,1) both;
  }

  .metric-card {
    background: var(--blanco);
    border: 1px solid var(--borde);
    border-radius: 16px;
    padding: 1.25rem;
    position: relative;
    overflow: hidden;
    transition: transform 0.25s, box-shadow 0.25s;
    cursor: default;
  }

  .metric-card:hover {
    transform: translateY(-4px);
    box-shadow: var(--sombra2);
  }

  .metric-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 3px;
    border-radius: 16px 16px 0 0;
  }

  .metric-card.azul::before { background: linear-gradient(90deg, var(--azul), var(--azul-claro)); }
  .metric-card.verde::before { background: linear-gradient(90deg, var(--verde), var(--verde-claro)); }
  .metric-card.ambar::before { background: linear-gradient(90deg, var(--ambar), var(--ambar-claro)); }
  .metric-card.morado::before { background: linear-gradient(90deg, var(--morado), var(--morado-claro)); }

  .metric-icon {
    width: 40px; height: 40px;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    margin-bottom: 0.75rem;
    font-size: 18px;
  }

  .metric-card.azul .metric-icon { background: rgba(27,79,216,0.1); color: var(--azul); }
  .metric-card.verde .metric-icon { background: rgba(11,138,90,0.1); color: var(--verde); }
  .metric-card.ambar .metric-icon { background: rgba(194,90,11,0.1); color: var(--ambar); }
  .metric-card.morado .metric-icon { background: rgba(91,33,182,0.1); color: var(--morado); }

  .metric-num {
    font-family: 'Syne', sans-serif;
    font-size: 32px;
    font-weight: 800;
    line-height: 1;
    margin-bottom: 4px;
  }

  .metric-card.azul .metric-num { color: var(--azul); }
  .metric-card.verde .metric-num { color: var(--verde); }
  .metric-card.ambar .metric-num { color: var(--ambar); }
  .metric-card.morado .metric-num { color: var(--morado); }

  .metric-label { font-size: 13px; color: var(--texto3); font-weight: 400; }

  /* ===== SECCIONES ===== */
  .section-grid {
    display: grid;
    grid-template-columns: 1.1fr 0.9fr;
    gap: 1.25rem;
    margin-bottom: 1.25rem;
    animation: fadeUp 0.7s 0.3s cubic-bezier(0.22,1,0.36,1) both;
  }

  .card {
    background: var(--blanco);
    border: 1px solid var(--borde);
    border-radius: 20px;
    padding: 1.5rem;
    box-shadow: var(--sombra);
  }

  .card-header {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 1.25rem;
  }

  .card-icon {
    width: 36px; height: 36px;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 16px;
    flex-shrink: 0;
  }

  .card-title {
    font-family: 'Syne', sans-serif;
    font-size: 15px;
    font-weight: 700;
    color: var(--texto);
  }

  /* ===== UNIDADES ===== */
  .unidad {
    border: 1px solid var(--borde);
    border-radius: 14px;
    padding: 1rem 1.1rem;
    margin-bottom: 0.75rem;
    cursor: pointer;
    transition: all 0.3s cubic-bezier(0.22,1,0.36,1);
    position: relative;
    overflow: hidden;
  }

  .unidad:last-child { margin-bottom: 0; }

  .unidad::before {
    content: '';
    position: absolute;
    left: 0; top: 0; bottom: 0;
    width: 4px;
    border-radius: 4px 0 0 4px;
    transition: width 0.3s;
  }

  .unidad.u1::before { background: var(--azul); }
  .unidad.u2::before { background: var(--verde); }
  .unidad.u3::before { background: var(--ambar); }

  .unidad:hover, .unidad.active {
    transform: translateX(4px);
    box-shadow: var(--sombra);
  }

  .unidad:hover::before, .unidad.active::before { width: 6px; }

  .unidad-head {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 5px;
  }

  .unidad-titulo {
    font-family: 'Syne', sans-serif;
    font-size: 13.5px;
    font-weight: 700;
    color: var(--texto);
    padding-left: 10px;
  }

  .sem-badge {
    font-size: 11px;
    font-weight: 600;
    padding: 3px 9px;
    border-radius: 100px;
    white-space: nowrap;
  }

  .u1 .sem-badge { background: rgba(27,79,216,0.1); color: var(--azul); }
  .u2 .sem-badge { background: rgba(11,138,90,0.1); color: var(--verde); }
  .u3 .sem-badge { background: rgba(194,90,11,0.1); color: var(--ambar); }

  .unidad-desc {
    font-size: 12px;
    color: var(--texto3);
    padding-left: 10px;
    margin-bottom: 8px;
    line-height: 1.5;
  }

  .tags {
    display: flex;
    flex-wrap: wrap;
    gap: 5px;
    padding-left: 10px;
  }

  .tag {
    font-size: 11px;
    padding: 2px 9px;
    border-radius: 100px;
    border: 1px solid var(--borde);
    color: var(--texto2);
    background: var(--fondo);
    transition: all 0.2s;
  }

  .unidad:hover .tag { border-color: rgba(27,79,216,0.25); }

  .progress-wrap { padding-left: 10px; margin-top: 8px; }

  .progress-track {
    height: 3px;
    background: var(--fondo2);
    border-radius: 3px;
    overflow: hidden;
  }

  .progress-fill {
    height: 100%;
    border-radius: 3px;
    width: 0;
    transition: width 1.2s cubic-bezier(0.22,1,0.36,1);
  }

  .u1 .progress-fill { background: linear-gradient(90deg, var(--azul), var(--azul-claro)); }
  .u2 .progress-fill { background: linear-gradient(90deg, var(--verde), var(--verde-claro)); }
  .u3 .progress-fill { background: linear-gradient(90deg, var(--ambar), var(--ambar-claro)); }

  /* ===== NIVELES ===== */
  .nivel-item {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 0.75rem 0;
    border-bottom: 1px solid var(--borde);
    cursor: pointer;
    transition: all 0.2s;
    border-radius: 8px;
    padding-left: 8px;
    padding-right: 8px;
  }

  .nivel-item:last-child { border-bottom: none; }
  .nivel-item:hover { background: var(--fondo); transform: translateX(3px); }

  .nivel-badge {
    width: 38px; height: 38px;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-family: 'Syne', sans-serif;
    font-size: 14px;
    font-weight: 800;
    flex-shrink: 0;
  }

  .n1 .nivel-badge { background: rgba(27,79,216,0.12); color: var(--azul); }
  .n2 .nivel-badge { background: rgba(11,138,90,0.12); color: var(--verde); }
  .n3 .nivel-badge { background: rgba(194,90,11,0.12); color: var(--ambar); }

  .nivel-info { flex: 1; }
  .nivel-nombre {
    font-family: 'Syne', sans-serif;
    font-size: 13.5px;
    font-weight: 700;
    color: var(--texto);
    margin-bottom: 2px;
  }
  .nivel-sub { font-size: 12px; color: var(--texto3); }

  .nivel-stars {
    display: flex;
    gap: 3px;
  }

  .star { font-size: 14px; }
  .n1 .star { color: var(--azul); }
  .n2 .star { color: var(--verde); }
  .n3 .star { color: var(--ambar); }

  /* ===== FILA COMPLETA ===== */
  .full-row {
    margin-bottom: 1.25rem;
    animation: fadeUp 0.7s 0.45s cubic-bezier(0.22,1,0.36,1) both;
  }

  /* ===== ADDIE ===== */
  .addie-strip {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    gap: 10px;
  }

  .addie-box {
    border-radius: 14px;
    padding: 1rem;
    position: relative;
    overflow: hidden;
    cursor: pointer;
    transition: transform 0.25s, box-shadow 0.25s;
  }

  .addie-box:hover { transform: translateY(-4px); box-shadow: var(--sombra2); }

  .addie-box::after {
    content: '';
    position: absolute;
    bottom: -20px; right: -20px;
    width: 70px; height: 70px;
    border-radius: 50%;
    opacity: 0.15;
  }

  .addie-box.ad1 { background: linear-gradient(135deg, #EEF2FF, #E0E7FF); }
  .addie-box.ad2 { background: linear-gradient(135deg, #F3E8FF, #EDE9FE); }
  .addie-box.ad3 { background: linear-gradient(135deg, #ECFDF5, #D1FAE5); }
  .addie-box.ad4 { background: linear-gradient(135deg, #FFFBEB, #FEF3C7); }
  .addie-box.ad5 { background: linear-gradient(135deg, #E0F2FE, #BAE6FD); }

  .addie-box.ad1::after { background: var(--azul); }
  .addie-box.ad2::after { background: var(--morado); }
  .addie-box.ad3::after { background: var(--verde); }
  .addie-box.ad4::after { background: var(--ambar); }
  .addie-box.ad5::after { background: #0EA5E9; }

  .addie-letra {
    font-family: 'Syne', sans-serif;
    font-size: 28px;
    font-weight: 800;
    line-height: 1;
    margin-bottom: 4px;
  }

  .ad1 .addie-letra { color: var(--azul); }
  .ad2 .addie-letra { color: var(--morado); }
  .ad3 .addie-letra { color: var(--verde); }
  .ad4 .addie-letra { color: var(--ambar); }
  .ad5 .addie-letra { color: #0369A1; }

  .addie-nombre {
    font-family: 'Syne', sans-serif;
    font-size: 12px;
    font-weight: 700;
    margin-bottom: 6px;
  }

  .ad1 .addie-nombre { color: var(--azul-oscuro); }
  .ad2 .addie-nombre { color: var(--morado); }
  .ad3 .addie-nombre { color: var(--verde); }
  .ad4 .addie-nombre { color: var(--ambar); }
  .ad5 .addie-nombre { color: #0369A1; }

  .addie-texto { font-size: 11.5px; color: var(--texto2); line-height: 1.5; }

  /* ===== GRID 3 ===== */
  .grid3 {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 1.25rem;
    margin-bottom: 1.25rem;
    animation: fadeUp 0.7s 0.6s cubic-bezier(0.22,1,0.36,1) both;
  }

  /* ===== COMPETENCIAS ===== */
  .comp-item {
    display: flex;
    gap: 10px;
    align-items: flex-start;
    padding: 0.65rem 0;
    border-bottom: 1px solid var(--borde);
    cursor: pointer;
    transition: all 0.2s;
    border-radius: 8px;
    padding-left: 6px;
  }

  .comp-item:last-child { border-bottom: none; }
  .comp-item:hover { background: var(--fondo); transform: translateX(3px); }

  .comp-dot {
    width: 30px; height: 30px;
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-size: 13px;
    flex-shrink: 0;
    margin-top: 1px;
  }

  .comp-nombre {
    font-family: 'Syne', sans-serif;
    font-size: 12.5px;
    font-weight: 700;
    color: var(--texto);
    margin-bottom: 2px;
  }

  .comp-desc { font-size: 11.5px; color: var(--texto3); line-height: 1.4; }

  /* ===== COMUNICACION ===== */
  .comm-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 8px;
  }

  .comm-item {
    background: var(--fondo);
    border: 1px solid var(--borde);
    border-radius: 12px;
    padding: 0.85rem;
    display: flex;
    gap: 10px;
    align-items: flex-start;
    cursor: pointer;
    transition: all 0.25s;
  }

  .comm-item:hover { background: var(--blanco); transform: translateY(-2px); box-shadow: var(--sombra); }

  .comm-icon-wrap {
    width: 34px; height: 34px;
    border-radius: 9px;
    display: flex; align-items: center; justify-content: center;
    font-size: 15px;
    flex-shrink: 0;
  }

  .comm-nombre { font-family: 'Syne', sans-serif; font-size: 12.5px; font-weight: 700; color: var(--texto); margin-bottom: 2px; }
  .comm-desc { font-size: 11px; color: var(--texto3); line-height: 1.4; }

  /* ===== RUBRICA ===== */
  .full-row-rubrica {
    animation: fadeUp 0.7s 0.75s cubic-bezier(0.22,1,0.36,1) both;
    margin-bottom: 1.25rem;
  }

  .rubrica-table { width: 100%; border-collapse: collapse; }

  .rubrica-table th {
    font-family: 'Syne', sans-serif;
    font-size: 12px;
    font-weight: 700;
    color: var(--texto3);
    text-align: left;
    padding: 8px 10px;
    background: var(--fondo);
    border-bottom: 2px solid var(--borde);
  }

  .rubrica-table th:first-child { border-radius: 10px 0 0 0; }
  .rubrica-table th:last-child { border-radius: 0 10px 0 0; text-align: center; }

  .rubrica-table td {
    font-size: 12px;
    padding: 9px 10px;
    vertical-align: top;
    border-bottom: 1px solid var(--borde);
    color: var(--texto2);
    line-height: 1.45;
    transition: background 0.2s;
  }

  .rubrica-table tr:hover td { background: var(--fondo); }
  .rubrica-table tr:last-child td { border-bottom: none; }

  .rubrica-table td:first-child {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 12.5px;
    color: var(--texto);
    white-space: nowrap;
  }

  .pts-cell {
    text-align: center;
    font-family: 'Syne', sans-serif;
    font-size: 15px;
    font-weight: 800;
    color: var(--azul) !important;
  }

  .excelente-badge {
    display: inline-block;
    background: rgba(11,138,90,0.1);
    color: var(--verde);
    font-size: 10px;
    font-weight: 600;
    padding: 2px 7px;
    border-radius: 100px;
    margin-bottom: 3px;
    font-family: 'Syne', sans-serif;
  }

  /* ===== ACTIVIDADES ===== */
  .actividad-card {
    background: var(--fondo);
    border: 1px solid var(--borde);
    border-radius: 14px;
    padding: 1rem 1.1rem;
    margin-bottom: 0.75rem;
    cursor: pointer;
    transition: all 0.25s;
    position: relative;
    overflow: hidden;
  }

  .actividad-card:last-child { margin-bottom: 0; }
  .actividad-card:hover { background: var(--blanco); box-shadow: var(--sombra); transform: translateY(-2px); }

  .actividad-head {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 6px;
  }

  .actividad-titulo {
    font-family: 'Syne', sans-serif;
    font-size: 13px;
    font-weight: 700;
    color: var(--texto);
  }

  .actividad-sem {
    font-size: 11px;
    color: var(--texto3);
    font-weight: 500;
  }

  .actividad-desc { font-size: 12px; color: var(--texto2); line-height: 1.5; margin-bottom: 8px; }

  .actividad-producto {
    display: flex;
    align-items: center;
    gap: 6px;
    font-size: 11.5px;
    color: var(--texto2);
    background: var(--blanco);
    border: 1px solid var(--borde);
    border-radius: 8px;
    padding: 5px 10px;
  }

  .producto-icon { font-size: 13px; }

  /* ===== FOOTER ===== */
  .footer-section {
    background: linear-gradient(135deg, var(--azul-oscuro), var(--azul));
    border-radius: 20px;
    padding: 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    animation: fadeUp 0.7s 0.9s cubic-bezier(0.22,1,0.36,1) both;
    box-shadow: var(--sombra2);
  }

  .footer-texto h3 {
    font-family: 'Syne', sans-serif;
    font-size: 18px;
    font-weight: 800;
    color: #fff;
    margin-bottom: 4px;
  }

  .footer-texto p { font-size: 13px; color: rgba(255,255,255,0.65); }

  .footer-meta {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    gap: 4px;
  }

  .footer-meta span { font-size: 12px; color: rgba(255,255,255,0.6); }

  .footer-meta strong {
    font-family: 'Syne', sans-serif;
    font-size: 14px;
    color: #fff;
    font-weight: 700;
  }

  /* ===== ANIMACIONES ===== */
  @keyframes slideDown {
    from { opacity: 0; transform: translateY(-30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes countUp {
    from { opacity: 0; transform: scale(0.5); }
    to { opacity: 1; transform: scale(1); }
  }

  .count-anim { animation: countUp 0.6s cubic-bezier(0.34,1.56,0.64,1) both; }

  /* ===== TOOLTIPS ===== */
  [data-tip] {
    position: relative;
  }

  [data-tip]::after {
    content: attr(data-tip);
    position: absolute;
    bottom: calc(100% + 8px);
    left: 50%;
    transform: translateX(-50%);
    background: var(--texto);
    color: #fff;
    font-size: 11px;
    padding: 5px 10px;
    border-radius: 6px;
    white-space: nowrap;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.2s;
    z-index: 10;
  }

  [data-tip]:hover::after { opacity: 1; }

  /* ===== RESPONSIVE ===== */
  @media (max-width: 768px) {
    .metrics-row { grid-template-columns: repeat(2, 1fr); }
    .section-grid { grid-template-columns: 1fr; }
    .addie-strip { grid-template-columns: repeat(2, 1fr); }
    .grid3 { grid-template-columns: 1fr; }
    .comm-grid { grid-template-columns: 1fr; }
    .hero { padding: 2rem 1.5rem; }
    .footer-section { flex-direction: column; gap: 1rem; align-items: flex-start; }
    .footer-meta { align-items: flex-start; }
  }
</style>
</head>
<body>

<div class="wrapper">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-tag">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/></svg>
      Misión 002 · Énfasis I
    </div>
    <h1>Aprendiendo con <span>Juego:</span><br>IA para Educadores</h1>
    <p class="hero-sub">Diseño del Syllabus de un Curso Virtual · Maestría en Recursos Digitales Aplicados a la Educación · Universidad de Cartagena</p>
    <div class="hero-pills">
      <span class="pill">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
        Entrega: 17 mayo 2026
      </span>
      <span class="pill">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>
        Máx. 4 estudiantes
      </span>
      <span class="pill">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>
        Neiva, Huila · Docentes rurales
      </span>
      <span class="pill">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
        6 semanas · Asincrónico
      </span>
    </div>
  </div>

  <!-- MÉTRICAS -->
  <div class="metrics-row">
    <div class="metric-card azul" data-tip="Tres unidades con progresión">
      <div class="metric-icon">📚</div>
      <div class="metric-num count-anim" id="m1">3</div>
      <div class="metric-label">Unidades temáticas</div>
    </div>
    <div class="metric-card verde" data-tip="ChatGPT, Canva IA, Quizlet...">
      <div class="metric-icon">🤖</div>
      <div class="metric-num count-anim" id="m2" style="animation-delay:0.1s">9+</div>
      <div class="metric-label">Herramientas de IA</div>
    </div>
    <div class="metric-card ambar" data-tip="Explorador → Innovador → Maestro">
      <div class="metric-icon">🏆</div>
      <div class="metric-num count-anim" id="m3" style="animation-delay:0.2s">3</div>
      <div class="metric-label">Niveles de logro</div>
    </div>
    <div class="metric-card morado" data-tip="Foros, correo, chat, videoconferencia">
      <div class="metric-icon">💬</div>
      <div class="metric-num count-anim" id="m4" style="animation-delay:0.3s">4</div>
      <div class="metric-label">Canales de comunicación</div>
    </div>
  </div>

  <!-- UNIDADES + NIVELES -->
  <div class="section-grid">
    <div class="card">
      <div class="card-header">
        <div class="card-icon" style="background:rgba(27,79,216,0.1);color:var(--azul)">📋</div>
        <span class="card-title">Unidades del Curso</span>
      </div>

      <div class="unidad u1 active" onclick="toggleUnidad(this)">
        <div class="unidad-head">
          <span class="unidad-titulo">Unidad 1 · Conociendo a la IA: De extraña a aliada</span>
          <span class="sem-badge">Sem. 1–2</span>
        </div>
        <div class="unidad-desc">Qué es la IA, mitos y verdades, IA en la educación y ética del uso en contextos pedagógicos.</div>
        <div class="tags">
          <span class="tag">ChatGPT</span>
          <span class="tag">Copilot</span>
          <span class="tag">Google Bard</span>
          <span class="tag">Nearpod</span>
        </div>
        <div class="progress-wrap">
          <div class="progress-track">
            <div class="progress-fill" style="width:33%"></div>
          </div>
        </div>
      </div>

      <div class="unidad u2" onclick="toggleUnidad(this)">
        <div class="unidad-head">
          <span class="unidad-titulo">Unidad 2 · La IA en mis clases: Crear y evaluar</span>
          <span class="sem-badge">Sem. 3–4</span>
        </div>
        <div class="unidad-desc">Creación de contenido con IA, evaluación adaptativa y retroalimentación automatizada.</div>
        <div class="tags">
          <span class="tag">Canva IA</span>
          <span class="tag">Quizlet</span>
          <span class="tag">Magic School AI</span>
        </div>
        <div class="progress-wrap">
          <div class="progress-track">
            <div class="progress-fill" style="width:33%"></div>
          </div>
        </div>
      </div>

      <div class="unidad u3" onclick="toggleUnidad(this)">
        <div class="unidad-head">
          <span class="unidad-titulo">Unidad 3 · Diseño lúdico con IA: Juegos que enseñan</span>
          <span class="sem-badge">Sem. 5–6</span>
        </div>
        <div class="unidad-desc">Juegos educativos con IA, gamificación en el aula y desarrollo del producto final.</div>
        <div class="tags">
          <span class="tag">Educaplay</span>
          <span class="tag">Genially</span>
          <span class="tag">Kahoot + IA</span>
          <span class="tag">Loom</span>
        </div>
        <div class="progress-wrap">
          <div class="progress-track">
            <div class="progress-fill" style="width:34%"></div>
          </div>
        </div>
      </div>
    </div>

    <div style="display:flex;flex-direction:column;gap:1.25rem;">

      <div class="card">
        <div class="card-header">
          <div class="card-icon" style="background:rgba(194,90,11,0.1);color:var(--ambar)">🎮</div>
          <span class="card-title">Niveles de Gamificación</span>
        </div>

        <div class="nivel-item n1" onclick="pulse(this)">
          <div class="nivel-badge">1</div>
          <div class="nivel-info">
            <div class="nivel-nombre">Explorador</div>
            <div class="nivel-sub">Primeros retos · Unidad 1</div>
          </div>
          <div class="nivel-stars">
            <span class="star">★</span>
          </div>
        </div>

        <div class="nivel-item n2" onclick="pulse(this)">
          <div class="nivel-badge">2</div>
          <div class="nivel-info">
            <div class="nivel-nombre">Innovador</div>
            <div class="nivel-sub">Crea con IA · Unidad 2</div>
          </div>
          <div class="nivel-stars">
            <span class="star">★</span>
            <span class="star">★</span>
          </div>
        </div>

        <div class="nivel-item n3" onclick="pulse(this)">
          <div class="nivel-badge">3</div>
          <div class="nivel-info">
            <div class="nivel-nombre">Maestro Digital</div>
            <div class="nivel-sub">Producto final · Unidad 3</div>
          </div>
          <div class="nivel-stars">
            <span class="star">★</span>
            <span class="star">★</span>
            <span class="star">★</span>
          </div>
        </div>
      </div>

      <div class="card">
        <div class="card-header">
          <div class="card-icon" style="background:rgba(11,138,90,0.1);color:var(--verde)">🎯</div>
          <span class="card-title">Propósito</span>
        </div>
        <p style="font-size:13px;color:var(--texto2);line-height:1.6;">Fortalecer las <strong style="color:var(--texto)">competencias digitales</strong> de docentes rurales mediante la exploración crítica de herramientas de <strong style="color:var(--texto)">Inteligencia Artificial</strong>, integrando <strong style="color:var(--texto)">gamificación</strong> y aprendizaje basado en juegos.</p>
      </div>

    </div>
  </div>

  <!-- ADDIE -->
  <div class="full-row">
    <div class="card">
      <div class="card-header">
        <div class="card-icon" style="background:rgba(91,33,182,0.1);color:var(--morado)">⚙️</div>
        <span class="card-title">Modelo de Diseño Instruccional — ADDIE</span>
      </div>
      <div class="addie-strip">
        <div class="addie-box ad1" onclick="pulse(this)">
          <div class="addie-letra">A</div>
          <div class="addie-nombre">Análisis</div>
          <div class="addie-texto">Diagnóstico a docentes rurales. 78% sin experiencia en IA. Recursos móviles y offline.</div>
        </div>
        <div class="addie-box ad2" onclick="pulse(this)">
          <div class="addie-letra">D</div>
          <div class="addie-nombre">Diseño</div>
          <div class="addie-texto">Resultados de aprendizaje por unidad. Herramientas de bajo consumo de datos.</div>
        </div>
        <div class="addie-box ad3" onclick="pulse(this)">
          <div class="addie-letra">D</div>
          <div class="addie-nombre">Desarrollo</div>
          <div class="addie-texto">Videos en Loom, infografías en Canva, interactivos en Genially. Revisión por pares.</div>
        </div>
        <div class="addie-box ad4" onclick="pulse(this)">
          <div class="addie-letra">I</div>
          <div class="addie-nombre">Implementación</div>
          <div class="addie-texto">Plataforma Moodle · 6 semanas · Videoconferencias quincenales via Google Meet.</div>
        </div>
        <div class="addie-box ad5" onclick="pulse(this)">
          <div class="addie-letra">E</div>
          <div class="addie-nombre">Evaluación</div>
          <div class="addie-texto">Formativa: retos y foros. Sumativa: actividad con IA + rúbrica + autoevaluación.</div>
        </div>
      </div>
    </div>
  </div>

  <!-- COMPETENCIAS + COMUNICACION + ACTIVIDADES -->
  <div class="grid3">

    <div class="card">
      <div class="card-header">
        <div class="card-icon" style="background:rgba(27,79,216,0.1);color:var(--azul)">✅</div>
        <span class="card-title">Competencias MEN</span>
      </div>

      <div class="comp-item" onclick="pulse(this)">
        <div class="comp-dot" style="background:rgba(27,79,216,0.1);color:var(--azul)">💻</div>
        <div>
          <div class="comp-nombre">Tecnológica</div>
          <div class="comp-desc">Selecciona herramientas IA pertinentes al contexto rural</div>
        </div>
      </div>

      <div class="comp-item" onclick="pulse(this)">
        <div class="comp-dot" style="background:rgba(11,138,90,0.1);color:var(--verde)">🏫</div>
        <div>
          <div class="comp-nombre">Pedagógica</div>
          <div class="comp-desc">Diseña actividades con IA integrada al currículo</div>
        </div>
      </div>

      <div class="comp-item" onclick="pulse(this)">
        <div class="comp-dot" style="background:rgba(91,33,182,0.1);color:var(--morado)">💬</div>
        <div>
          <div class="comp-nombre">Comunicativa</div>
          <div class="comp-desc">Participa activamente en comunidades virtuales</div>
        </div>
      </div>

      <div class="comp-item" onclick="pulse(this)">
        <div class="comp-dot" style="background:rgba(194,90,11,0.1);color:var(--ambar)">🔍</div>
        <div>
          <div class="comp-nombre">Investigativa</div>
          <div class="comp-desc">Reflexiona y rediseña su práctica pedagógica</div>
        </div>
      </div>

      <div class="comp-item" onclick="pulse(this)">
        <div class="comp-dot" style="background:rgba(11,138,90,0.08);color:var(--verde)">⚙️</div>
        <div>
          <div class="comp-nombre">Gestión</div>
          <div class="comp-desc">Planifica el uso de IA en su institución rural</div>
        </div>
      </div>
    </div>

    <div class="card">
      <div class="card-header">
        <div class="card-icon" style="background:rgba(27,79,216,0.1);color:var(--azul)">📡</div>
        <span class="card-title">Comunicación</span>
      </div>

      <div class="comm-grid">
        <div class="comm-item" onclick="pulse(this)">
          <div class="comm-icon-wrap" style="background:rgba(27,79,216,0.1);color:var(--azul)">💬</div>
          <div>
            <div class="comm-nombre">Foros</div>
            <div class="comm-desc">Avisos · Preguntas · Reflexión pedagógica</div>
          </div>
        </div>
        <div class="comm-item" onclick="pulse(this)">
          <div class="comm-icon-wrap" style="background:rgba(194,90,11,0.1);color:var(--ambar)">📧</div>
          <div>
            <div class="comm-nombre">Correo</div>
            <div class="comm-desc">Comunicaciones formales e individuales</div>
          </div>
        </div>
        <div class="comm-item" onclick="pulse(this)">
          <div class="comm-icon-wrap" style="background:rgba(11,138,90,0.1);color:var(--verde)">💭</div>
          <div>
            <div class="comm-nombre">Chat Moodle</div>
            <div class="comm-desc">Consultas rápidas y grupos</div>
          </div>
        </div>
        <div class="comm-item" onclick="pulse(this)">
          <div class="comm-icon-wrap" style="background:rgba(91,33,182,0.1);color:var(--morado)">📹</div>
          <div>
            <div class="comm-nombre">Google Meet</div>
            <div class="comm-desc">Sesiones quincenales · 60 min</div>
          </div>
        </div>
      </div>
    </div>

    <div class="card">
      <div class="card-header">
        <div class="card-icon" style="background:rgba(194,90,11,0.1);color:var(--ambar)">📝</div>
        <span class="card-title">Actividades y Productos</span>
      </div>

      <div class="actividad-card" onclick="pulse(this)">
        <div class="actividad-head">
          <span class="actividad-titulo">🎯 Reto Nivel 1: Trivia IA</span>
          <span class="actividad-sem">Sem. 1–2</span>
        </div>
        <div class="actividad-desc">Trivia gamificada + foro de reflexión «Lo que creía vs. lo que descubrí».</div>
        <div class="actividad-producto">
          <span class="producto-icon">📄</span>
          Reflexión 200 palabras + 2 respuestas
        </div>
      </div>

      <div class="actividad-card" onclick="pulse(this)">
        <div class="actividad-head">
          <span class="actividad-titulo">🎨 Galería de Materiales</span>
          <span class="actividad-sem">Sem. 3–4</span>
        </div>
        <div class="actividad-desc">Material educativo creado con IA, compartido con retroalimentación de pares.</div>
        <div class="actividad-producto">
          <span class="producto-icon">🖼️</span>
          Material IA publicado + descripción
        </div>
      </div>

      <div class="actividad-card" onclick="pulse(this)">
        <div class="actividad-head">
          <span class="actividad-titulo">🏆 Producto Final</span>
          <span class="actividad-sem">Sem. 5–6</span>
        </div>
        <div class="actividad-desc">Actividad gamificada con IA para aplicar con sus propios estudiantes.</div>
        <div class="actividad-producto">
          <span class="producto-icon">🎬</span>
          Juego IA + Video 3–5 min + Autoevaluación
        </div>
      </div>
    </div>
  </div>

  <!-- RÚBRICA -->
  <div class="full-row-rubrica">
    <div class="card">
      <div class="card-header">
        <div class="card-icon" style="background:rgba(11,138,90,0.1);color:var(--verde)">📊</div>
        <span class="card-title">Rúbrica de Valoración</span>
      </div>
      <div style="overflow-x:auto;">
        <table class="rubrica-table">
          <thead>
            <tr>
              <th style="width:18%">Criterio</th>
              <th style="width:27%">Excelente</th>
              <th style="width:23%">Satisfactorio</th>
              <th style="width:23%">En proceso</th>
              <th style="width:9%">Pts</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>Propósito y Justificación</td>
              <td><span class="excelente-badge">★ Óptimo</span><br>Articulado con necesidades educativas y literatura especializada actualizada.</td>
              <td>Claro pero con fundamentación teórica limitada.</td>
              <td>Vago o descontextualizado de la realidad.</td>
              <td class="pts-cell">/ 5</td>
            </tr>
            <tr>
              <td>Modelo ADDIE</td>
              <td><span class="excelente-badge">★ Óptimo</span><br>Todas las fases aplicadas con coherencia y detalle al curso diseñado.</td>
              <td>Fases descritas con inconsistencias parciales en la aplicación.</td>
              <td>Mencionado pero sin aplicación real al curso.</td>
              <td class="pts-cell">/ 5</td>
            </tr>
            <tr>
              <td>Escenarios y Ambiente</td>
              <td><span class="excelente-badge">★ Óptimo</span><br>Estrategias claras, rol del tutor, netiqueta y recursos de navegación.</td>
              <td>Rol del tutor o pautas de interacción poco precisas.</td>
              <td>Sin articulación al proceso formativo.</td>
              <td class="pts-cell">/ 5</td>
            </tr>
            <tr>
              <td>Contenidos y Actividades</td>
              <td><span class="excelente-badge">★ Óptimo</span><br>Coherencia pedagógica, actividades variadas y articuladas con objetivos.</td>
              <td>Articulación parcial con los objetivos del curso.</td>
              <td>Superficiales o no responden a los objetivos.</td>
              <td class="pts-cell">/ 5</td>
            </tr>
            <tr>
              <td>Rúbrica</td>
              <td><span class="excelente-badge">★ Óptimo</span><br>Clara, específica y permite valorar el aprendizaje de forma formativa.</td>
              <td>Criterios generales o parcialmente coherentes.</td>
              <td>Criterios vagos o insuficientes para valorar.</td>
              <td class="pts-cell">/ 5</td>
            </tr>
            <tr>
              <td>Normas APA</td>
              <td><span class="excelente-badge">★ Óptimo</span><br>APA 7ª ed. correcta. Redacción clara y académicamente pertinente.</td>
              <td>Errores menores de citación o formato APA.</td>
              <td>APA inconsistente, redacción imprecisa.</td>
              <td class="pts-cell">/ 5</td>
            </tr>
          </tbody>
        </table>
      </div>
      <div style="margin-top:1rem;padding:0.75rem 1rem;background:rgba(27,79,216,0.05);border-radius:10px;border:1px solid rgba(27,79,216,0.12);display:flex;align-items:center;justify-content:space-between;">
        <span style="font-size:13px;color:var(--texto2)">Puntaje total del curso</span>
        <span style="font-family:'Syne',sans-serif;font-size:20px;font-weight:800;color:var(--azul)">30 puntos</span>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer-section">
    <div class="footer-texto">
      <h3>Aprendiendo con Juego: IA para Educadores</h3>
      <p>Maestría en Recursos Digitales Aplicados a la Educación · Universidad de Cartagena</p>
    </div>
    <div class="footer-meta">
      <span>Modelo instruccional</span>
      <strong>ADDIE</strong>
      <span>Entrega</span>
      <strong>17 de mayo de 2026</strong>
    </div>
  </div>

</div>

<script>
  function toggleUnidad(el) {
    document.querySelectorAll('.unidad').forEach(u => u.classList.remove('active'));
    el.classList.add('active');
  }

  function pulse(el) {
    el.style.transform = 'scale(0.97)';
    setTimeout(() => { el.style.transform = ''; }, 180);
  }

  // Animar barras de progreso al cargar
  window.addEventListener('load', () => {
    setTimeout(() => {
      document.querySelectorAll('.progress-fill').forEach(bar => {
        const target = bar.style.width;
        bar.style.width = '0';
        setTimeout(() => { bar.style.width = target; }, 100);
      });
    }, 600);
  });

  // Contador animado para métricas
  function animateCount(el, target, suffix, delay) {
    const isPlus = target === '9+';
    const num = isPlus ? 9 : parseInt(target);
    setTimeout(() => {
      let current = 0;
      const step = Math.ceil(num / 20);
      const timer = setInterval(() => {
        current = Math.min(current + step, num);
        el.textContent = current + (isPlus ? '+' : '');
        if (current >= num) clearInterval(timer);
      }, 50);
    }, delay);
  }

  animateCount(document.getElementById('m1'), '3', '', 300);
  animateCount(document.getElementById('m2'), '9+', '+', 400);
  animateCount(document.getElementById('m3'), '3', '', 500);
  animateCount(document.getElementById('m4'), '4', '', 600);
</script>
</body>
</html>
