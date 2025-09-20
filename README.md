<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Problema de ejemplo - Distribución de aire</title>
    <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
    <script id="MathJax-script" async
        src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
    </script>
    <style>
        body { font-family: 'Georgia', serif; margin: 20px; line-height: 1.6; color: #222; }
        .line { margin: 15px 0; font-size: 1.05em; }
        .eq { color: #004d99; font-size: 1.15em; padding: 5px; border-left: 3px solid #007BFF; background-color: #f9f9f9; }
        .resultado { font-weight: bold; color: #28a745; margin-top: 20px; font-size: 1.25em; text-align: center; }
        #nextBtn {
            margin-top: 20px;
            padding: 12px 25px;
            background-color: #007BFF;
            border: none;
            color: white;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1em;
            transition: background-color 0.3s ease;
        }
        #nextBtn:hover { background-color: #0056b3; }
        .problema {
            background: #f1f3f5;
            border: 1px solid #ced4da;
            padding: 20px;
            margin-bottom: 25px;
            border-radius: 8px;
            font-size: 1.05em;
        }
        h2 { border-bottom: 2px solid #007BFF; padding-bottom: 10px; color: #007BFF; }
    </style>
</head>
<body>
    <h2>Problema de ejemplo - Distribución de aire</h2>
    <div class="problema">
        <p>
        En una sección de un sistema de distribución de aire, el fluido se encuentra a 
        \(14.7 \,\text{psia}\) y \(100^{\circ}\text{F}\), con una velocidad promedio de 
        \(1200 \,\tfrac{\text{ft}}{\text{min}}\). El conducto en esta parte es cuadrado, de 
        \(12 \,\text{in}\) por lado. <br><br>
        En otra sección, el conducto es circular con un diámetro de 
        \(D_2 = 18 \,\text{in}\), y en ella se ha medido una velocidad de 
        \(900 \,\tfrac{\text{ft}}{\text{min}}\). <br><br>
        Calcular:  
        <br>(a) La densidad del aire en la sección circular.  
        <br>(b) El flujo másico de aire en libras por hora. <br><br>
        Datos:  
        \(\rho_1 = 2.20 \times 10^{-3} \,\tfrac{\text{slug}}{\text{ft}^3}\),  
        \(\gamma_1 = 7.09 \times 10^{-2} \,\tfrac{\text{lb}}{\text{ft}^3}\).
        </p>
    </div>

    <div id="solution"></div>
    <button id="nextBtn">Mostrar siguiente paso</button>

    <script>
        const pasos = [
            // --- PARTE A: Cálculo de la densidad ---
            {tipo:"intro", texto:"1) Se aplica la ecuación de continuidad para gases: \\( \\rho_1 A_1 v_1 = \\rho_2 A_2 v_2 \\)."},
            {tipo:"eq", linea:0, partes:["\\rho_1 A_1 v_1 = \\rho_2 A_2 v_2"]},
            
            {tipo:"intro", texto:"2) Despejando la densidad en la sección circular, se obtiene:"},
            {tipo:"eq", linea:1, partes:["\\rho_2 = \\rho_1 \\; \\dfrac{A_1}{A_2} \\; \\dfrac{v_1}{v_2}"]},

            {tipo:"intro", texto:"3) Se calculan las áreas de ambas secciones. Para la sección cuadrada de lado \\(12 \\, \\text{in}\\):"},
            {tipo:"eq", linea:2, partes:["A_1 = (12 \\, \\text{in})^2 = 144 \\, \\text{in}^2"]},

            {tipo:"intro", texto:"Área de la sección circular, con diámetro \\(D_2 = 18 \\, \\text{in}\\):"},
            {tipo:"eq", linea:3, partes:["A_2 = \\dfrac{\\pi D_2^2}{4} = \\dfrac{\\pi (18 \\, \\text{in})^2}{4} = 254 \\, \\text{in}^2"]},

            {tipo:"intro", texto:"4) Sustituyendo en la ecuación de continuidad con los valores numéricos:"},
            {tipo:"eq", linea:4, partes:["\\rho_2 = \\left(2.20 \\times 10^{-3} \\; \\tfrac{\\text{slug}}{\\text{ft}^3}\\right) \\cdot \\dfrac{144}{254} \\cdot \\dfrac{1200}{900}"]},
            
            {tipo:"eq", linea:5, partes:["\\rho_2 = (2.20 \\times 10^{-3}) \\cdot (0.567) \\cdot (1.333) \\; \\tfrac{\\text{slug}}{\\text{ft}^3}"]},
            
            {tipo:"add", linea:5, texto:"= 1.66 \\times 10^{-3} \\; \\tfrac{\\text{slug}}{\\text{ft}^3}"},
            
            {tipo:"final", texto:"Resultado (a): <br> \\[ \\rho_2 = 1.66 \\times 10^{-3} \\; \\tfrac{\\text{slug}}{\\text{ft}^3} \\]"},

            // --- PARTE B: Cálculo del flujo másico ---
            {tipo:"intro", texto:"5) El flujo másico \\(W\\) se puede calcular en cualquiera de las dos secciones. Usando la sección cuadrada:"},
            {tipo:"eq", linea:6, partes:["W = \\gamma_1 A_1 v_1"]},

            {tipo:"intro", texto:"6) Sustituyendo los valores y aplicando los factores de conversión correspondientes:"},
            {tipo:"eq", linea:7, partes:["W = \\left(7.09 \\times 10^{-2} \\; \\tfrac{\\text{lb}}{\\text{ft}^3}\\right) \\cdot (144 \\, \\text{in}^2) \\cdot \\dfrac{1200 \\, \\text{ft}}{\\text{min}} \\cdot \\dfrac{1 \\, \\text{ft}^2}{144 \\, \\text{in}^2} \\cdot \\dfrac{60 \\, \\text{min}}{1 \\, \\text{h}}"]},

            {tipo:"add", linea:7, texto:"= 5100 \\; \\tfrac{\\text{lb}}{\\text{h}}"},
            
            {tipo:"final", texto:"Resultado (b): <br> \\[ W = 5100 \\; \\tfrac{\\text{lb}}{\\text{h}} \\]"}
        ];

        const contenedor = document.getElementById('solution');
        const lineas = [];
        let pasoActual = 0;

        document.getElementById('nextBtn').addEventListener('click', () => {
            if(pasoActual >= pasos.length){
                alert("Ya se mostró toda la solución.");
                document.getElementById('nextBtn').style.display = 'none';
                return;
            }
            const paso = pasos[pasoActual];

            if(paso.tipo === "intro"){
                const p = document.createElement('p');
                p.className = 'line';
                p.innerHTML = paso.texto;
                contenedor.appendChild(p);
            } else if(paso.tipo === "eq"){
                const p = document.createElement('p');
                p.className = 'line eq';
                p.dataset.linea = paso.linea;
                p.innerHTML = `\\[ ${paso.partes.join(' ')} \\]`;
                contenedor.appendChild(p);
                lineas[paso.linea] = {elemento: p, partes:[...paso.partes]};
            } else if(paso.tipo === "add"){
                const linea = lineas[paso.linea];
                if (linea) {
                    linea.partes.push(paso.texto);
                    linea.elemento.innerHTML = `\\[ ${linea.partes.join(' ')} \\]`;
                }
            } else if (paso.tipo === "final") {
                const p = document.createElement('p');
                p.className = 'resultado';
                p.innerHTML = paso.texto;
                contenedor.appendChild(p);
            }
            MathJax.typesetPromise();
            pasoActual++;
        });
    </script>
</body>
</html>
