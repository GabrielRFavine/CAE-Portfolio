# 🏎️ Projeto 01: Simulação Aerodinâmica Externa Veicular (CFD)

## 1. Objetivo do Projeto
Este projeto tem como objetivo realizar a análise de Dinâmica dos Fluidos Computacional (CFD) do escoamento externo de ar ao redor de uma geometria veicular simplificada. O foco da análise é avaliar os fenômenos aerodinâmicos, 
mapear as zonas de separação do escoamento na região traseira e determinar os coeficientes globais de **Arrasto** e **Sustentação/Downforce**.

---

## 2. Geometria e Domínio do Fluido

* **Modelo Geométrico:** Geometria veicular simplificada (*sedan/hatchback* para estudos aerodinâmicos).
* **Tratamento de Geometria (*Defeaturing*):** Supressão de detalhes não estruturais ao escoamento (maçanetas, folga de portas e retrovisores) para garantia de uma malha de alta qualidade na camada limite.
* **Domínio Computacional (Túnel de Vento Virtual):**
  * **Montante (Inlet):** 3x o comprimento do veículo.
  * **Jusante (Outlet):** 6x o comprimento do veículo para permitir o pleno desenvolvimento da esteira turbulenta.
  * **Largura e Altura:** Dimensionados para garantir taxa de bloqueio (*Blockage Ratio*) inferior a 3%.

---

## 3. Condições de Contorno e Modelo Fisico

Simulação configurada no **ANSYS Fluent**:

* **Entrada de Ar (*Velocity Inlet*):** Velocidade constante de -----.
* **Saída (*Pressure Outlet*):** Pressão manométrica de -----.
* **Solo (*Moving Wall*):** Parede móvel na mesma velocidade do fluxo de ar ------ para simular a condição real de rolagem do piso.
* **Superfície do Veículo (*No-Slip Wall*):** Parede com condição de não-deslizamento.
* **Modelo de Turbulência:** ------ (*Shear Stress Transport*), ideal para prever com precisão a separação do fluxo sob gradientes adversos de pressão.

---

## 4. Estudo de Malha e Camada Limite (*Inflation Layer*)

Para capturar corretamente os efeitos do gradiente de velocidade próximo à superfície do veículo, foi configurada uma malha não estruturada com refinamento na camada limite (*Inflation*):

| Parâmetro | Configuração / Valor |
| :--- | :--- |
| **Tipo de Elementos** | Tetraédricos no domínio livre + Prismáticos na camada limite |
| **Primeira Camada (First Layer Height)** | Calculado para garantir ------- nas superfícies críticas |
| **Camadas de Inflamento (Inflation Layers)** | 10 a 15 camadas com taxa de crescimento de 1.2 |
| **Nº Total de Elementos** | ~2.800.000 elementos (pós-convergência) |

---

## 5. Resultados e Visualização do Escoamento

### Coeficientes Aerodinâmicos Obtidos
* **Coeficiente de Arrasto:** `[Insira o valor, ex: 0.312]`
* **Coeficiente de Sustentação:** `[Insira o valor, ex: 0.045]`

### Análise Qualitativa
![Linhas de Corrente e Esteira de Turbulência](./imagens/streamlines.png)
*(Espaço para print das Streamlines / Vetores de Velocidade)*

1. **Região Dianteira:** Alta pressão estática no para-choque frontal e capô (ponto de estagnação).
2. **Esteira Traseira:** Formação de zonas de recirculação de baixa pressão (*vórtices traseiros*), principal fonte geradora de arrasto por pressão.

---

## 6. Conclusões de Engenharia
* O modelo ------- permitiu identificar com clareza o ponto de separação do escoamento no teto e na tampa do porta-malas.
* A esteira de baixa pressão criada na traseira responde por mais de 60% do arrasto total do veículo.
* **Proposta para CAD / Próximo Passo:** Avaliar a inclusão de um pequeno *spoiler* traseiro para gerenciar a esteira e aplicar um raio de curvatura maior na transição do teto para reduzir o descolamento precoce do fluxo.
